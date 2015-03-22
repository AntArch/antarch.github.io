---
Date: 2014-09-25 14:47
Title: Creating AddressBase+ from AdressBase Premium
Category: GIS, addressing, UK
Tags:  GIS, addressing, UK
layout: post
---

#Creating AB+ from ABPrem

Use the [OS Addressing products attribute mapping](http://www.ordnancesurvey.co.uk/docs/support/os-addressing-products-attribute-mapping.pdf) and the [AddressBase technical specification](http://www.ordnancesurvey.co.uk/docs/technical-specifications/addressbase-premium-technical-specification-csv.pdf) as references.

The debate about ABP and AB+ still goes on. To help this I have pulled together a query to get an AB+ view from the ABP data. It's not an exact match (it's just quick and dirty) but most things are there.

Count of records in ABPREM_BLPU

```sql
select count(*) from ABPREM_BLPU;
```

giving 311159. This is an important figure. The end should match this!

##BLPU and DPA

According to the technical spec there is a 1:(0,1) relationship between BLPU and DPA

```sql
select
	blpu.CHANGE_TYPE,
		blpu.UPRN,
		blpu.BLPU_STATE,
		blpu.BLPU_STATE_DATE,
		blpu.PARENT_UPRN,
		blpu.X_COORDINATE,
		blpu.Y_COORDINATE,
		blpu.RPC,
		blpu.LOCAL_CUSTODIAN_CODE,
		blpu.START_DATE,
		blpu.END_DATE,
		blpu.LAST_UPDATE_DATE,
		blpu.ENTRY_DATE,
		blpu.POSTAL_ADDRESS,
		blpu.POSTCODE_LOCATOR,
		blpu.MULTI_OCC_COUNT,
		dpa.RM_UDPRN,
		dpa.ORGANISATION_NAME,
		dpa.DEPARTMENT_NAME,
		dpa.SUB_BUILDING_NAME,
		dpa.BUILDING_NAME,
		dpa.BUILDING_NUMBER,
		dpa.DEP_THOROUGHFARE_NAME,
		dpa.THOROUGHFARE_NAME,
		dpa.DOU_DEP_LOCALITY,
		dpa.DEP_LOCALITY,
		dpa.POST_TOWN,
		dpa.POSTCODE,
		dpa.POSTCODE_TYPE,
		dpa.WELSH_DEP_THOROUGHFARE_NAME,
		dpa.WELSH_THOROUGHFARE_NAME,
		dpa.WELSH_DOU_DEP_LOCALITY,
		dpa.WELSH_DEP_LOCALITY,
		dpa.WELSH_POST_TOWN,
		dpa.PO_BOX_NUMBER,
		dpa.PROCESS_DATE
	FROM
		ABPREM_BLPU blpu
	LEFT OUTER JOIN
		ABPREM_DELIVERYPTADDRESS dpa
	ON
		blpu.UPRN = dpa.UPRN;
```

So lets count

```sql
select
	count(*)
	FROM
		ABPREM_BLPU blpu
	LEFT OUTER JOIN
		ABPREM_DELIVERYPTADDRESS dpa
	ON
		blpu.UPRN = dpa.UPRN;
```

giving 311160. This means instead of a 1:1 match between BLPU and DPA which is what the model states we have a 1: many relationship.

Lets look at this

```sql
select 
	UPRN, count(1)
	from 
		ABPREM_DELIVERYPTADDRESS
	group by 
		UPRN
	having 
		count (UPRN) > 1;
```

Produces 69 duplicate DPAs with the same UPRN. This is not good news.

Lets look at some of these:

```sql
select 
	a.*
	from 
		ABPREM_DELIVERYPTADDRESS a,
		(select 
			UPRN
			from 
				ABPREM_DELIVERYPTADDRESS
			group by 
				UPRN
			having 
				count (UPRN) > 1) b
	where a.UPRN = b.UPRN
	order by 
		a.UPRN;
```	

These appear to be duplicate records in every respect EXCEPT they have a different number in the PRO_ORDER field. We can get around this by using a distinct select.

```sql
select
	dpa.*
	FROM
		ABPREM_DELIVERYPTADDRESS dpa
	JOIN
		(select distinct
			UPRN
			FROM 
				ABPREM_DELIVERYPTADDRESS) dup
	ON
		dup.UPRN = dpa.UPRN;
```

We should be able to slot this into the earlier query

Lets look at this

```sql
select 
	UPRN, count(1)
	from 
		(select distinct
			UPRN
			FROM 
				ABPREM_DELIVERYPTADDRESS)
			group by 
				UPRN
			having 
				count (UPRN) > 1;
```

Produces O duplicate DPAs with the same UPRN. This is much better news.

There are ways to fix (including deleting duplicates in the source) this but I'm going for quick and dirty. I will materialise the table and then delete the duplicates:

* Materialise the table as SPA_BLPU_DPA

```sql
create table SPA_BLPU_DPA
	as
		select
			blpu.CHANGE_TYPE,
				blpu.UPRN,
				blpu.BLPU_STATE,
				blpu.BLPU_STATE_DATE,
				blpu.PARENT_UPRN,
				blpu.X_COORDINATE,
				blpu.Y_COORDINATE,
				blpu.RPC,
				blpu.LOCAL_CUSTODIAN_CODE,
				blpu.START_DATE,
				blpu.END_DATE,
				blpu.LAST_UPDATE_DATE,
				blpu.ENTRY_DATE,
				blpu.POSTAL_ADDRESS,
				blpu.POSTCODE_LOCATOR,
				blpu.MULTI_OCC_COUNT,
				dpa.RM_UDPRN,
				dpa.ORGANISATION_NAME,
				dpa.DEPARTMENT_NAME,
				dpa.SUB_BUILDING_NAME,
				dpa.BUILDING_NAME,
				dpa.BUILDING_NUMBER,
				dpa.DEP_THOROUGHFARE_NAME,
				dpa.THOROUGHFARE_NAME,
				dpa.DOU_DEP_LOCALITY,
				dpa.DEP_LOCALITY,
				dpa.POST_TOWN,
				dpa.POSTCODE,
				dpa.POSTCODE_TYPE,
				dpa.WELSH_DEP_THOROUGHFARE_NAME,
				dpa.WELSH_THOROUGHFARE_NAME,
				dpa.WELSH_DOU_DEP_LOCALITY,
				dpa.WELSH_DEP_LOCALITY,
				dpa.WELSH_POST_TOWN,
				dpa.PO_BOX_NUMBER,
				dpa.PROCESS_DATE
			FROM
				ABPREM_BLPU blpu
			LEFT OUTER JOIN
				ABPREM_DELIVERYPTADDRESS dpa
			ON
				blpu.UPRN = dpa.UPRN;

commit;
```

and delete the duplicates

```sql
--------------------------------------------------------
-- FORCE UPRN to be unique!
--------------------------------------------------------
delete from SPA_BLPU_DPA
  where rowid in (select rowid
    from SPA_BLPU_DPA
    minus
      select min(rowid)
      from SPA_BLPU_DPA
    group by UPRN);

commit;

```

we can now count the table

```sql
select
	count (*)
	from
		SPA_BLPU_DPA;
```

31159. thats better

**This is a problem with AddressPlace Premium). According to the [ER model](http://www.ordnancesurvey.co.uk/docs/technical-specifications/addressbase-premium-technical-specification-csv.pdf)^[see page 6] there should be 1:(0,1) relationship between BLPU and DPA tables. This is clearly wrong**

##CLASSIFICATION and BLPU

According to the technical spec there is a 1:many relationship between BLPU and Classification 

Lets look at the many side of things.....

```sql
select 
	count(*)
	from 
		(select 
			UPRN
			from 
				ABPREM_CLASSIFICATION
			group by 
				UPRN
			having 
				count (UPRN) > 1);
```

There are 576 multiple classifications from 4.2 million

So this is going to be an annoyingly regular thing. We can get rid of the 1 to manys with the following:

```sql
select 
	UPRN,
	max(CLASSIFICATION_CODE) CLASS
	from 
		ABPREM_CLASSIFICATION
	group by 
		UPRN;  
```

which allows us to join to SPA_BLPU_DPA as follows

```sql
select
	blpudpa.*,
		class.CLASS
	FROM
		SPA_BLPU_DPA blpudpa
	LEFT OUTER JOIN
		(select 
			UPRN,
			max(CLASSIFICATION_CODE) CLASS
			from 
				ABPREM_CLASSIFICATION
			group by 
				UPRN) class
	ON
		blpudpa.UPRN = class.UPRN;
```

##Application cross reference

According to the technical spec there is a 1:many relationship between BLPU and Application cross reference

The primary fields are UPRN, SOURCE and CROSS_REFERENCE. Ideally each UPRN, SOURCE, CROSS_REFERENCE combination should be unique:

```
select 
	UPRN,
		SOURCE, 
		CROSS_REFERENCE,
		count(1)
	from 
		ABPREM_APPXREF
	group by 
		UPRN,
		SOURCE, 
		CROSS_REFERENCE
	having 
		count (UPRN) > 1);
```

Produces duplicates. Again not good :-(

The best way of dealing with this is to look at it as a pivot table. We can pivot this data out and give it the required headings using the query below:

```sql
select 
	*
	from
		(select 
			UPRN,
				SOURCE, 
				CROSS_REFERENCE
			from 
				ABPREM_APPXREF)
	pivot
		(min(CROSS_REFERENCE)
		for SOURCE
		in 
			('7666MA' as OS_ADDRESS_TOID,
			'7666MT' as OS_TOPO_TOID,
			'7666MI' AS OS_ROADLINK_TOID,
			'7666VC' AS VOA_CT_RECORD,
			'7666VN' AS VOA_NDR_RECORD,
			'7666OW' AS WARD_CODE,
			'7666OP' AS PARISH_CODE));
```

which allows us to join to SPA_BLPU_DPA as follows:

```sql
select
	blpudpa.*,
		xref.OS_ADDRESS_TOID,
		xref.OS_TOPO_TOID,
		xref.OS_ROADLINK_TOID,
		xref.VOA_CT_RECORD,
		xref.VOA_NDR_RECORD,
		xref.WARD_CODE,
		xref.PARISH_CODE
	FROM
		SPA_BLPU_DPA blpudpa
	LEFT OUTER JOIN
		(select 
			*
			from
				(select 
					UPRN,
						SOURCE, 
						CROSS_REFERENCE
					from 
						ABPREM_APPXREF)
			pivot
				(min(CROSS_REFERENCE)
				for SOURCE
				in 
					('7666MA' as OS_ADDRESS_TOID,
					'7666MT' as OS_TOPO_TOID,
					'7666MI' AS OS_ROADLINK_TOID,
					'7666VC' AS VOA_CT_RECORD,
					'7666VN' AS VOA_NDR_RECORD,
					'7666OW' AS WARD_CODE,
					'7666OP' AS PARISH_CODE))) xref
	ON
		blpudpa.UPRN = xref.UPRN;
```

##ORGANISATION and BLPU

According to the technical spec there is a 1:many relationship between BLPU and ORGANISATION 

Lets look at the many side of things.....

```sql
select 
	count(*)
	from 
		(select 
			UPRN
			from 
				ABPREM_ORGANISATION
			group by 
				UPRN
			having 
				count (UPRN) > 1);
```

There are 4 multiple ORGANISATIONs from 87,772.

We can get rid of the 1 to manys with the following:

```sql
select 
	UPRN,
	max(ORGANISATION) ORGANISATION
	from 
		ABPREM_ORGANISATION
	group by 
		UPRN;  
```

which allows us to join to SPA_BLPU_DPA as follows

```sql
select
	blpudpa.*,
		org.ORGANISATION
	FROM
		SPA_BLPU_DPA blpudpa
	LEFT OUTER JOIN
		(select 
			UPRN,
			max(ORGANISATION) ORGANISATION
			from 
				ABPREM_ORGANISATION
			group by 
				UPRN) org
	ON
		blpudpa.UPRN = org.UPRN;
```
##LPI and BLPU

According to the technical spec there is a 1:many relationship between BLPU and LPI 

However, we already have the table ABP_SINGLE_ADDRESS which should have resolved most of these many issues.

Lets look at the many side of things.....

```sql
select 
	count(*)
	from 
		(select 
			UPRN
			from 
				ABP_SINGLE_ADDRESS
			group by 
				UPRN
			having 
				count (UPRN) > 1);
```

This is null. So we can join the tables together with SPA_BLPU_DPA as follows

```sql
select
	blpudpa.*,
		lpi.SAO_TEXT,
		lpi.SAO_START_NUMBER,
		lpi.SAO_START_SUFFIX,
		lpi.SAO_END_NUMBER,
		lpi.SAO_END_SUFFIX,
		lpi.PAO_TEXT,
		lpi.PAO_START_NUMBER,
		lpi.PAO_START_SUFFIX,
		lpi.PAO_END_NUMBER,
		lpi.PAO_END_SUFFIX,
		lpi.STREET_DESCRIPTION,
		lpi.LOCALITY_NAME,
		lpi.POSTCODE_LOCATOR,
		lpi.GEO_SINGLE_ADDRESS_LABEL
	FROM
		SPA_BLPU_DPA blpudpa
	LEFT OUTER JOIN
		ABP_SINGLE_ADDRESS lpi
	ON
		blpudpa.UPRN = lpi.UPRN;
```

##Bringing it all together

Basically just plug them all together into a big long multiple join statement:-)

```sql
select
	blpudpa.*,
		class.CLASS,
		org.ORGANISATION,
		lpi.SAO_TEXT,
		lpi.SAO_START_NUMBER,
		lpi.SAO_START_SUFFIX,
		lpi.SAO_END_NUMBER,
		lpi.SAO_END_SUFFIX,
		lpi.PAO_TEXT,
		lpi.PAO_START_NUMBER,
		lpi.PAO_START_SUFFIX,
		lpi.PAO_END_NUMBER,
		lpi.PAO_END_SUFFIX,
		lpi.STREET_DESCRIPTION,
		lpi.LOCALITY_NAME,
		lpi.POSTCODE_LOCATOR,
		lpi.GEO_SINGLE_ADDRESS_LABEL,
		xref.OS_ADDRESS_TOID,
		xref.OS_TOPO_TOID,
		xref.OS_ROADLINK_TOID,
		xref.VOA_CT_RECORD,
		xref.VOA_NDR_RECORD,
		xref.WARD_CODE,
		xref.PARISH_CODE
	FROM
		SPA_BLPU_DPA blpudpa
	LEFT OUTER JOIN
		(select 
			UPRN,
			max(CLASSIFICATION_CODE) CLASS
			from 
				ABPREM_CLASSIFICATION
			group by 
				UPRN) class
	ON
		blpudpa.UPRN = class.UPRN
	LEFT OUTER JOIN
		(select 
			UPRN,
			max(ORGANISATION) ORGANISATION
			from 
				ABPREM_ORGANISATION
			group by 
				UPRN) org
	ON
		blpudpa.UPRN = org.UPRN
	LEFT OUTER JOIN
		ABP_SINGLE_ADDRESS lpi
	ON
		blpudpa.UPRN = lpi.UPRN
	LEFT OUTER JOIN
		(select 
			*
			from
				(select 
					UPRN,
						SOURCE, 
						CROSS_REFERENCE
					from 
						ABPREM_APPXREF)
			pivot
				(min(CROSS_REFERENCE)
				for SOURCE
				in 
					('7666MA' as OS_ADDRESS_TOID,
					'7666MT' as OS_TOPO_TOID,
					'7666MI' AS OS_ROADLINK_TOID,
					'7666VC' AS VOA_CT_RECORD,
					'7666VN' AS VOA_NDR_RECORD,
					'7666OW' AS WARD_CODE,
					'7666OP' AS PARISH_CODE))) xref
	ON
		blpudpa.UPRN = xref.UPRN;
```

This can be used to create a new table SPA_ABPLUS_CLONE

```sql
create table SPA_ABPLUS_CLONE as 

	select
		blpudpa.*,
			class.CLASS,
			org.ORGANISATION,
			lpi.SAO_TEXT,
			lpi.SAO_START_NUMBER,
			lpi.SAO_START_SUFFIX,
			lpi.SAO_END_NUMBER,
			lpi.SAO_END_SUFFIX,
			lpi.PAO_TEXT,
			lpi.PAO_START_NUMBER,
			lpi.PAO_START_SUFFIX,
			lpi.PAO_END_NUMBER,
			lpi.PAO_END_SUFFIX,
			lpi.STREET_DESCRIPTION,
			lpi.LOCALITY_NAME,
			lpi.POSTCODE_LOCATOR as LPI_POSTCODE_LOCATOR,
			lpi.GEO_SINGLE_ADDRESS_LABEL,
			xref.OS_ADDRESS_TOID,
			xref.OS_TOPO_TOID,
			xref.OS_ROADLINK_TOID,
			xref.VOA_CT_RECORD,
			xref.VOA_NDR_RECORD,
			xref.WARD_CODE,
			xref.PARISH_CODE
		FROM
			SPA_BLPU_DPA blpudpa
		LEFT OUTER JOIN
			(select 
				UPRN,
				max(CLASSIFICATION_CODE) CLASS
				from 
					ABPREM_CLASSIFICATION
				group by 
					UPRN) class
		ON
			blpudpa.UPRN = class.UPRN
		LEFT OUTER JOIN
			(select 
				UPRN,
				max(ORGANISATION) ORGANISATION
				from 
					ABPREM_ORGANISATION
				group by 
					UPRN) org
		ON
			blpudpa.UPRN = org.UPRN
		LEFT OUTER JOIN
			ABP_SINGLE_ADDRESS lpi
		ON
			blpudpa.UPRN = lpi.UPRN
		LEFT OUTER JOIN
			(select 
				*
				from
					(select 
						UPRN,
							SOURCE, 
							CROSS_REFERENCE
						from 
							ABPREM_APPXREF)
				pivot
					(min(CROSS_REFERENCE)
					for SOURCE
					in 
						('7666MA' as OS_ADDRESS_TOID,
						'7666MT' as OS_TOPO_TOID,
						'7666MI' AS OS_ROADLINK_TOID,
						'7666VC' AS VOA_CT_RECORD,
						'7666VN' AS VOA_NDR_RECORD,
						'7666OW' AS WARD_CODE,
						'7666OP' AS PARISH_CODE))) xref
		ON
			blpudpa.UPRN = xref.UPRN;

commit;

```

To wrap this all up we should then count the records

```sql
Select count(*) from SPA_ABPLUS_CLONE
```

at 311159 records. Our work here is done.
