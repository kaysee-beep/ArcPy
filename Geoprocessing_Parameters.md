# Open Python Window in ArcGIS Pro

1. Import ArcPy
2. Set the workspace
3. Allow outputs to overwrite existing files
4. Set the coordinate system using WKID (well-known ID) where NAD83 UTM Zone 17N : 26917
5. Check current workspace
```python
import arcpy
arcpy.env.workspace = r"C:\file_location\file_name.gdb"
arcpy.env.overwriteOutput = True
arcpy.env.outputCoordinateSystem = arcpy.SpatialReference(WKID)
print(arcpy.env.workspace)
```

# ArcPy Functions
Help function `print(help(arcpy.analysis.X))` will print list of parameters for specific function and explain what each parameter means. Any parameters with { } indicates non-required fields. 
# Examples of Common Geoprocessing Parameters
*Set optional parameters by using an empty string `dissolve_option = "",` OR not including it in code block OR `"",` in line of code*

**Buffer Analysis**
```python
arcpy.analysis.buffer(
  in_features = "filename.shp",
  out_feature_class = "filename_analysis.shp",
  buffer_distance_or_field = "X Feet",
)
```
**Clip, Erase, Identity, Intersect, SelectAnalysis**

Parameter Functions:
`arcpy.analysis.clip`, `arcpy.analysis.erase`, `arcpy.analysis.identity`, `arcpy.analysis.intersect`, arcpy.analysis.select`
```python
arcpy.analysis.X(
  in_features = "filename.shp",
  out_feature_class = "filename_analysis.shp"
)
```
**Spatial Join Analysis**
```python
arcpy.analysis.spatialjoin(
  target_features = "X",
  join_features = "X",
  out_feature_class = "X_X_join.shp"
)
```
Optional parameters include: `join_operation`, `join_type`, `field_mapping`, `match_option`, `search_radius`, and `distance_field_name`
  
  
