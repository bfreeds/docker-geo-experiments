# Notes  
These are working notes for progress / lesssons learned while working to test WFS through Geoserver  


Need to setup data geoserver data store  

Try mounting a volume with `docker run`.
Run the container & enter bash shell to see if shapefiles are mounted:  
`docker run --rm -ti -v data:/geodata kartoza/geoserver /bin/bash`  
==> `geodata` directory exists, but no child files were copied over  

Needed to give the host directory's full path:  
`docker run --rm -ti -v /home/brandyn/projects/geoserver/data:/geodata kartoza/geoserver /bin/bash`  

So, the command to start the container and keep it running:
`docker run -d --name 'geoserver' --link postgis:postgis -v /home/brandyn/projects/geoserver/data:/geodata -p 8080:8080 -t kartoza/geoserver`  

In Geoserver Admin:  
- Login with `admin` and password `geoserver`  
- Create workspace `test`  
- Create data store => from directory  
- Configure Layer  
- Use `localhost:8080/geoserver/ows?service=wfs&version=2.0&request=GetCapabilities`  
- Open a WFS connection in QGIS with that URL, access layer in QGIS
