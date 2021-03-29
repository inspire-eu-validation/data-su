# Basic test

**Purpose**: Verify that the spatial data set contains at least one Statistical Units feature.

**Prerequisites**

**Test method**

* Check that the set of [features](#features) in the spatial data set is not empty. Otherwise report [noFeature](#noFeature)

**Reference(s)**: 

* [TG DS-SU](./README.md#ref_TG_DS_SU) 5.4, 5.5

**Test type**: Automated

**Notes**

There is no requirement that we could reference in the Technical Guidelines. Maybe such a requirement should be added in the future revision?

## Messages

Identifier  |  Message text (parameters start with '$')
----------- | -------------------------------------------------------------------------
noFeature <a name="noFeature"/>  |  	The XML documents representing the spatial data set do not contain a feature of any of the spatial object types in the 'Statistical Units' application schemas. Therefore, the spatial data set cannot conform to this conformance class. If you have expected to find spatial objects from the application schema in the data set, please consult the statistics information to see the spatial object types that have been found.

## Contextual XPath references

The namespace prefixes used as described in [README.md](./README.md#namespaces).

Abbreviation                                          |  XPath expression
----------------------------------------------------- | ------------------------------------------------------------------
features <a name="features"></a>   |  //schema-element(su-vector:VectorStatisticalUnit) <br> OR <br>  //schema-element(su-vector:AreaStatisticalUnit) OR <br>  //schema-element(su-vector:StatisticalTesselation) OR <br>  //schema-element(su-vector:Evolution) OR <br>  //schema-element(su-grid:StatisticalGridCell) OR <br>  //schema-element(su-grid:StatisticalGrid)