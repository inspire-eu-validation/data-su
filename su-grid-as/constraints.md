# Constraints

**Purpose**: Verify that the features provided in the dataset adhere to the constraints specified in the INSPIRE application schema.

**Prerequisites**

**Test method**

The following check is performed for every feature in the dataset.

* Check that at least one of the attributes [code](#code), [geographicalPosition](#geographicalPosition), [gridPosition](#gridPosition) or [geometry](#geometry) is provided (spatialRepresentationConstraint).


The following check shall be manually performed for every feature in the dataset related to StatisticalGrid feature type:

* Check that if the [coordinate reference system](#EPSG) of the StatisticalGrid is a projected one, the resolution shall be a [length](length#). Otherwise, it shall be an [angle](angle#) (resolutionTypeConstraint).


The following checks shall be manually performed for every feature in the dataset related to StatisticalGridCell feature type:

* Check that the cell position is within the grid, according to its width and height (gridPositionRangeConstraint).

* Check that where several spatial representations are provided ([code](#code), [geographicalPosition](#geographicalPosition), [gridPosition](#gridPosition) and [geometry](#geometry)), they are consistent (spatialRepresentationsConsistencyConstraint).

* Check that the [code](#code) is composed of:
	(1) A coordinate reference system part, represented by the word CRS, followed by the EPSG code.
	(2) A resolution and position part:
		— If the coordinate reference system is projected, the word RES followed by the grid resolution in meters and the letter m. Then, the letter N followed by the northing value in meters, and the letter E followed by the easting value in meters.
		— If the coordinate reference system is not projected, the word RES followed by the grid resolution in degree-minute-second, followed by the word dms. Then the word LON followed by the longitude value in degree-minute-second, and word LAT followed by the latitude value in degree-minute-second.
		For both cases, the given position shall be the position of the lower left cell corner (cellCodeConstraint).


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)
* [TG DS-SU](./README.md#ref_TG_DS_SU) 5.3.3.1.1.; 5.3.3.1.2.

**Test type**: Automatic + Manual

**Notes** 

Verify that the OCL constraints that are specified in the UML model of the application schema are met, i.e. validate features against the constraints. For unmet constraints report [constraintViolation](#constraintViolation).

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
constraintViolation <a name="constraintViolation"/>  |  XML document '$filename', $featureType '$gmlid': The constraint '$constraint' is violated.

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                                               |  XPath expression                     |Multiplicity       |Voidable
---------------------------------------------------------- | ------------------------------------- | ------------------|----------
code<a name="code"></a> | //schema-element(su-grid:StatisticalGridCell)/su-grid:code| 1 | Yes
geographicalPosition<a name="geographicalPosition"></a> | //schema-element(su-grid:StatisticalGridCell)/su-grid:geographicalPosition| 1 | Yes
geometry<a name="geometry"></a> | //schema-element(su-grid:StatisticalGridCell)/su-grid:geometry| 1 | Yes
gridPosition<a name="gridPosition"></a> | //schema-element(su-grid:StatisticalGridCell)/su-grid:gridPosition| 0..1 | Yes
coordinate reference system<a name="EPSG"></a> | //schema-element(su-grid:StatisticalGrid)/su-grid:EPSGCode| 0..1 | No
length<a name="length"></a> | //schema-element(su-grid:StatisticalGrid)/su-grid:resolution/su-grid:StatisticalGridResolution/su-grid:lengthResolution| 0..1 | No
angle<a name="angle"></a> | //schema-element(su-grid:StatisticalGrid)/su-grid:resolution/su-grid:StatisticalGridResolution/su-grid:angleResolution| 0..1 | No