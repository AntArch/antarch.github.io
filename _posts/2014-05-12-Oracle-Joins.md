---
Date: 2014-05-12 13:00
Title: Oracle joins and ABP
Category: IT, Oracle, Joins
Tags: IT, Oracle, Joins
layout: post
---

# Metadata

This document is formatted using MarkDown

This work was done by Anthony Beck, [OrcID: 0000-0002-2991-811X](http://orcid.org/0000-0002-2991-811X).

Part of the series of *hating Oracle but having to work with it*

# Cross joins

Essentially the dot product. 

I need to create a cross join to see what combination of products I have based on tables in an Oracle Schema.

Currently I want to compare all things which are prefixed as 

* BUILDINGPOLYGON_
* ROADNETWORK_

```sql
select 
	a.TABLE_NAME as CLASS1, 
		b.TABLE_NAME as CLASS2 
	from 
		user_tables a 
	CROSS JOIN 
		user_tables b
	where 
		a.TABLE_NAME LIKE 'BUILDINGPOLYGON_%'
		AND a.TABLE_NAME NOT LIKE '%_O'
		AND b.TABLE_NAME LIKE 'ROADNETWORK_%'
		AND b.TABLE_NAME NOT LIKE '%_O';
```

If I add in new address elements I may want to add in an extra component:

* ADDRESSPOINT_
* BUILDINGPOLYGON_
* ROADNETWORK_

```sql
select 
	a.TABLE_NAME as CLASS1, 
		b.TABLE_NAME as CLASS2, 
		c.TABLE_NAME as CLASS3
	from 
		user_tables a 
	CROSS JOIN 
		user_tables b 
	CROSS JOIN 
		user_tables c
	where 
		a.TABLE_NAME LIKE 'ADDRESSPOINT_%'
		AND a.TABLE_NAME NOT LIKE '%_O'
		AND b.TABLE_NAME LIKE 'BUILDINGPOLYGON_%'
		AND b.TABLE_NAME NOT LIKE '%_O'
		and c.TABLE_NAME LIKE 'ROADNETWORK_%'
		AND c.TABLE_NAME NOT LIKE '%_O';
		
```

```sql
select 
	a.TABLE_NAME as CLASS1, 
		b.TABLE_NAME as CLASS2, 
		c.TABLE_NAME as CLASS3
	from 
		user_tables a 
		CROSS JOIN user_tables b 
		CROSS JOIN user_tables c
	where 
		a.TABLE_NAME LIKE 'BLD_PLY_%'
		AND a.TABLE_NAME NOT LIKE '%_O'
		AND b.TABLE_NAME LIKE 'ROD_NET_%'
		AND b.TABLE_NAME NOT LIKE '%_O'
		and c.TABLE_NAME LIKE 'ADD_CNT_%'
		AND c.TABLE_NAME NOT LIKE '%_O';
```

This means I can produce a table, *METADATA_CLASSPAIR* with 3 tuples:

CLASS_SOURCE|CLASS_NAME
----|----
BUILDING SOURCE|CLASS1
ROADNETWORK_SOURCE|CLASS2
ADDRESS SOURCE|CLASS3


This table is used when calling RadiusStudio. By doing it like this I can essentially call a template Radius Studio action and iterate directly over my CROSS JOIN rows. This means everything is generic.

# ABP in the ABP schema

It looks like the ingest sequence for ABP embeds the geomtry as 81989. 81989 is an old oracle name for OSGB projection (srid 27700)

To fix this I did the following:

* drop the index
* update ABPREM_BLPU p set p.geometry.sdo_srid=27700;
* COMMIT;
* Recreate the index

# ABP in the postaldeliveryinput schema

* Radius Studio converts the UPRN (number) to a string (either natively or using the built in function) as an exponential string


# Nearest Neighbour

```sql

set serveroutput on;
begin
  declare
    lt2 number :=0;
    lt1 number :=0;
    lt5 number :=0;
    lt10 number :=0;
    lt25 number :=0;
    lt50 number :=0;
    gt50 number :=0;
    counter number := 0;

begin

  for recs in 
	(
	select 
		street_intrstn_id,
			new_geom
		from
			t_street_intersection
		where 
			rownum < 100
	) loop

		for recs2 in 
			(select 
				recs.street_intrstn_id, 
					r.toid, 
					sdo_nn_distance(1) dist
				from
					itn.ITNRDND r
				where 
					sdo_nn
						(
						r.new_geom, 
						recs.new_geom,
						'sdo_batch_size=5',
						1
						) = 'TRUE'
					and rownum < 2
			) Loop

				if recs2.dist <= 1 then
					lt1 := lt1 + 1;
					elsif recs2.dist <= 2 then
						lt2 := lt2 + 1;
					elsif recs2.dist <= 5 then
						lt5 := lt5 + 1;
					elsif recs2.dist <= 10 then
						lt10 := lt10 + 1;
					elsif recs2.dist <= 25 then
						lt25 := lt25 + 1;
					elsif recs2.dist <= 50 then
						lt50 := lt50 + 1;
					else
						gt50 := gt50 + 1;
				end if;

				counter := counter+1;         

			end loop;

	end loop;

  dbms_output.put_line('Less than     1m '||to_char(lt1,'99999')||'   '||to_char(lt1/counter*100,'999.0')||'%');

  dbms_output.put_line('Less than     2m '||to_char(lt2,'99999')||'   '||to_char(lt2/counter*100,'999.0')||'%');

  dbms_output.put_line('Less than     5m '||to_char(lt5,'99999')||'   '||to_char(lt5/counter*100,'999.0')||'%');

  dbms_output.put_line('Less than    10m '||to_char(lt10,'99999')||'   '||to_char(lt10/counter*100,'999.0')||'%');

  dbms_output.put_line('Less than    25m '||to_char(lt25,'99999')||'   '||to_char(lt25/counter*100,'999.0')||'%');

  dbms_output.put_line('Less than    50m '||to_char(lt50,'99999')||'   '||to_char(lt50/counter*100,'999.0')||'%');

  dbms_output.put_line('Greater Than 50m '||to_char(gt50,'99999')||'   '||to_char(gt50/counter*100,'999.0')||'%');

  dbms_output.put_line('TOTAL            '||to_char(counter,'99999'));

  end;

end;

/
``` 
