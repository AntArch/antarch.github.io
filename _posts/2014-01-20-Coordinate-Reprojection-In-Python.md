Date: 2014-01-20 17:00
Title: Coordinate reprojection in python
Category: Python, Geo, Reprojection
Tags: Python, Geo, Reprojection
#Aims:
This post demonstrates how to transform/reproject co-ordinates under python



#URLs used:
* [all geo blog](http://all-geo.org/volcan01010/2012/11/change-coordinates-with-pyproj/)
* [Basemap Matplotlib Toolkit examples](http://matplotlib.org/basemap/users/examples.html)
* [Chair of information architecture](http://www.ia.arch.ethz.ch/lat-lon-to-ch-coordinates/)

I need to do some reprojections so have looked at a range of python libraries and shown some example. 

#reproject using pyproj
from [all geo blog](http://all-geo.org/volcan01010/2012/11/change-coordinates-with-pyproj/)


	import mpl_toolkits.basemap.pyproj as pyproj # Import the pyproj module
 
	# Define a projection with Proj4 notation, in this case an Icelandic grid
	isn2004=pyproj.Proj("+proj=lcc +lat_1=64.25 +lat_2=65.75 +lat_0=65 +lon_0=-19 +x_0=1700000 +y_0=300000 +no_defs +a=6378137 +rf=298.257222101 +to_meter=1")
 
	# Define some common projections using EPSG codes
	wgs84=pyproj.Proj("+init=EPSG:4326") # LatLon with WGS84 datum used by GPS units and Google Earth
	osgb36=pyproj.Proj("+init=EPSG:27700") # UK Ordnance Survey, 1936 datum
	UTM26N=pyproj.Proj("+init=EPSG:32626") # UTM coords, zone 26N, WGS84 datum
	UTM27N=pyproj.Proj("+init=EPSG:32627") # UTM coords, zone 27N, WGS84 datum
	UTM28N=pyproj.Proj("+init=EPSG:32628") # ... you get the picture

	# Do the projection
	isn2004(-19.700,63.983)
	#(1665725.2429655411, 186813.38847515779)
	#Obviously, you want to capture the output:

	# Assign output to variables x and y
	x, y = isn2004(-19.700,63.983)
	x
	#1665725.2429655411
	y
	#186813.38847515779
	#You can also do the inverse transform:

	isn2004(x, y, inverse=True)
	#(-19.699999999999999, 63.982999999999564)


#My problem - transforming the co-ordinates from the Irish grid to WGS84

Basically we need to do a transform function using pyproj

This is [relatively simple](http://www.ia.arch.ethz.ch/lat-lon-to-ch-coordinates/) (note I've updated the syntax):



	from pyproj import Proj, transform #from the pyproj library import Projection and transformation
	pWorld = Proj("+init=EPSG:4326") #define pWorld using [EPSG 4326](http://spatialreference.org/ref/epsg/4326/)
	pCH = Proj("+init=EPSG:21781") #define pCH using [EPSG 21781](http://spatialreference.org/ref/epsg/21781/)
	transform(pWorld,pCH, 47.4,8.5,0) #transform co-ordinates given in WGS84 into EPSG:21781


I need to convert from the Irish Grid into WGS84. I've been told that Ordnance Survey Ireland use [EPSG:29902](http://spatialreference.org/ref/epsg/29902/) but should be using [EPSG:29903](http://spatialreference.org/ref/epsg/29903/).

Our setup is as follows:

	from pyproj import Proj, transform #from the pyproj library import Projection and transformation
	pWorld = Proj("+init=EPSG:4326") #define pWorld using [EPSG 4326](http://spatialreference.org/ref/epsg/4326/)
    pTM65 = Proj("+init=EPSG:29902") #define pTM75 using [EPSG:29902](http://spatialreference.org/ref/epsg/29902/)
    pTM75 = Proj("+init=EPSG:29903") #define pTM75 using [EPSG:29903](http://spatialreference.org/ref/epsg/29903/)


To convert 284190	432472  using EPSG 29902

	Long, Lat = transform(pTM65,pWorld, 284190, 432472) #transform co-ordinates given in EPSG:29902 into WGS84
	print (Lat, Long)

Produces [55.132309809804454, -6.680823158964323](https://maps.google.co.uk/maps?q=55.132309809804454,+-6.680823158964323)

To convert 284190	432472  using EPSG 29903

	Long, Lat = transform(pTM75,pWorld, 284190, 432472) #transform co-ordinates given in EPSG:299023into WGS84
	print (Lat, Long)

Produces [55.132310246784726, -6.680823275968558](https://maps.google.co.uk/maps?q=55.132310246784726,+-6.680823275968558)

So all quite easy really. Now I just need to bring automate this onto a CSV file and plot in the folium library

#Basemap Matplotlib Toolkit

[Basemap Matplotlib Toolkit has some beautiful stuff](http://matplotlib.org/basemap/users/examples.html) 

#Plot contour lines on a basemap

	from mpl_toolkits.basemap import Basemap
	import matplotlib.pyplot as plt
	import numpy as np
	# set up orthographic map projection with
	# perspective of satellite looking down at 50N, 100W.
	# use low resolution coastlines.
	map = Basemap(projection='ortho',lat_0=45,lon_0=-100,resolution='l')
	# draw coastlines, country boundaries, fill continents.
	map.drawcoastlines(linewidth=0.25)
	map.drawcountries(linewidth=0.25)
	map.fillcontinents(color='coral',lake_color='aqua')
	# draw the edge of the map projection region (the projection limb)
	map.drawmapboundary(fill_color='aqua')
	# draw lat/lon grid lines every 30 degrees.
	map.drawmeridians(np.arange(0,360,30))
	map.drawparallels(np.arange(-90,90,30))
	# make up some data on a regular lat/lon grid.
	nlats = 73; nlons = 145; delta = 2.*np.pi/(nlons-1)
	lats = (0.5*np.pi-delta*np.indices((nlats,nlons))[0,:,:])
	lons = (delta*np.indices((nlats,nlons))[1,:,:])
	wave = 0.75*(np.sin(2.*lats)**8*np.cos(4.*lons))
	mean = 0.5*np.cos(2.*lats)*((np.sin(2.*lats))**2 + 2.)
	# compute native map projection coordinates of lat/lon grid.
	x, y = map(lons*180./np.pi, lats*180./np.pi)
	# contour data over the map.
	cs = map.contour(x,y,wave+mean,15,linewidths=1.5)
	plt.title('contour lines over filled continent background')
	plt.show()

