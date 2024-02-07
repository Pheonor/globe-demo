
1. Add a basic projection system
The Projection class allows to project and unproject between (lon,lat) and (x,y) coordinates based on zoom level to allow an adaptative projection if necessary.
The Projection class provides a method "isGlobe" to inform renderer if the selected projection is on globe or not.
A default projection should be define for backward compatibility ('mercator' by default).
Some methods and properties on the 'map' allows to change the active projection.
All call to 'mercatorXfromLng', 'mercatorYfromLat', 'lngFromMercatorX' and 'latFromMercatorY' should be replace by this projection system.
The 'Transform' class contains the active projection.

2. Add a Globe shader associated to a 'globe' projection
Create new shaders to transform the mercator projection into an allipsoid Globe.
This globe shader use the 'render to texture' approach.
It uses the same geometry tiles as the mercator map but transform into the shader.
Some matrix tranformation between the map and the globe should be created to pan arround the globe and put in place all tiles.
Texture coordinates should also be remap from the mercator projection to the globe projection.

3. Update the Tile loading mechanism for globe
Ensure all visible tile in globe mode are loaded properly with the good zoom level.
To ensure only visible tiles selection, a tile should be inside the view frustrum and not hidden by the globe.
Only close tiles should have the better resolution.

4. Fill the pole holes
Update the rendering process to draw specificaly poles and avoid holes.

5. Update symbol position for globe
Compute new symbol position for globe geometry and manage clutering or hiding into this projection.
Hides also symbols mask by the globe.

6. Add an atmospheric layer
Add an atmospheric layer only visible at low zoom and hided when close to the Earth.
This layer should be optionnal.

7. Add a stars layer
Add a background stars layers.
This layer should be optionnal.

8. Add an adaptative projection
This projection allow to switch from globe at low zoom level to mercator at high zoom level.
