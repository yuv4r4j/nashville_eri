# Nashville area Tornadoes Emergency Response Imagery

The National Geodetic Survey has published Emergency Response Imagery for the damage track from the 2020 tornadoes near the Nashville area.

The data are available as [cloud optimized geotiffs](https://www.cogeo.org/) on Amazon S3 at **s3://noaa-eri-pds/2020_Nashville_Tornado/**. The geotiffs can be used in GIS mapping software such as ArcGIS, QGIS, or explored with analysis software such as Python.

## How to get this data

The [AWS CLI](https://aws.amazon.com/cli/) can be used to access this data. No AWS account is necessary.

To list all of the available data:

```
aws s3 ls s3://noaa-eri-pds/2020_Nashville_Tornado/ --recursive --no-sign-request
```

To download a single geotiff file:

```
aws s3 cp s3://noaa-eri-pds/2020_Nashville_Tornado/20200307a_RGB/20200307aC0853600w361200n.tif . --no-sign-request
```

You can also access this data via HTTPS at [https://noaa-eri-pds.s3.amazonaws.com/index.html#2020_Nashville_Tornado/20200307a_RGB/](https://noaa-eri-pds.s3.amazonaws.com/index.html#2020_Nashville_Tornado/20200307a_RGB/)

NOAA provides a web map view of this data available at [https://storms.ngs.noaa.gov/storms/nashville/index.html#9/36.1800/-86.2000](https://storms.ngs.noaa.gov/storms/nashville/index.html#9/36.1800/-86.2000)

## Example of this data

![Example image from Nashville Tornadoes ERI](img/example.png)


