<!--fused:preview-->
<p align="center"><img src="https://fused-magic.s3.us-west-2.amazonaws.com/thumbnails/udfs-staging/DSM_Zonal_Stats.png" width="600" alt="UDF preview image"></p>

<!--fused:tags-->
Tags: `30-meter` `aws` `tutorial` `buildings`

<!--fused:readme-->
## Overview

This UDF calculate average DSM for every buildings in the United States. ALOS Global Digital Surface Model "ALOS World 3D - 30m (AW3D30)" captured by the PRISM optical sensor on the ALOS satellite, with a 30-meter horizontal resolution.

## External links
- [JAXA Digital Surface Model](https://data.earth.jaxa.jp/en/datasets/#/id/JAXA.EORC_ALOS.PRISM_AW3D30.v3.2_global)
- [STAC Collection File](https://s3.ap-northeast-1.wasabisys.com/je-pds/cog/v1/JAXA.EORC_ALOS.PRISM_AW3D30.v3.2_global/collection.json)

## Run this in any Jupyter Notebook

```python
import fused
import geopandas as gpd

udf_url = "https://github.com/fusedio/udfs/tree/main/public/DSM_Zonal_Stats"
udf = fused.load(udf_url)

bbox = gpd.GeoDataFrame.from_features(
    {"type": "FeatureCollection", "features": [{"id": "0", "type": "Feature", "properties": {"x": 5241, "y": 12667, "z": 15}, "geometry": {"type": "Polygon", "coordinates": [[[-124.1455078125, 41.77131167976406], [-124.1455078125, 41.73852846935915], [-124.189453125, 41.73852846935915], [-124.189453125, 41.77131167976406], [-124.1455078125, 41.77131167976406]]]}}]},
    crs="EPSG:4326"
)

gdf = udf.run_local(bbox=bbox)
gdf
```
