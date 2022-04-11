# Constraints

**Purpose**: Verify that the features provided in the dataset adhere to the constraints specified in the INSPIRE application schema.

**Prerequisites**

**Test method**

The following checks are performed for every feature in the dataset.

* Check that vector statistical units with a [reference geometry](#refGeomVSU) instance of [GM_MultiSurface](#GM_MultiSurfaceVSU) are instances of the specialised class AreaStatisticalUnit (AreaStatisticalUnitsConstraint). 

* Check that the [reference geometry](#refGeomASU) of an area statistical units is a [GM_MultiSurface](#GM_MultiSurfaceASU) or [GM_Surface](#GM_SurfaceASU) (Support for the additional geometry type GM_Surface was introduced due to the unclear wording of the related constraint. More info are available in the [following issue](https://github.com/INSPIRE-MIF/technical-guidelines/issues/38)).

* Check that the [mostDetailedScale](#mostDetailedScale) and [leastDetailedScale](#leastDetailedScale) fields are provided only for geometry descriptors with a type [generalisedGeometry](#generalisedGeometry) (GeneralisedGeometryConstraint).

* Check that, if provided, [mostDetailedScale](#mostDetailedScale) is smaller than [leastDetailedScale](#leastDetailedScale) (ScaleRelationConstraint).


The following checks shall be manually performed for every feature in the dataset related to the spatial object type Evolution:

* Evolution representations shall be consistent with the versions of the concerned objects.
* An evolution with a [typeValue](#typeValue) “creation” shall not have any [initial unit versions](#initialUnitVersions) and only one [final](#finalUnitVersions) one.
* An evolution with a [typeValue](#typeValue) “deletion” shall have one [initial unit versions](#initialUnitVersions) and no [final](#finalUnitVersions) one.
* An evolution with a [typeValue](#typeValue) “aggregation” shall have at least two [initial unit versions](#initialUnitVersions)s (the units to be aggregated) and a single [final](#finalUnitVersions) one (the resulting aggregation).
* An evolution with a [typeValue](#typeValue) “change” shall have one [initial unit versions](#initialUnitVersions) and one [final](#finalUnitVersions) one.
* An evolution with a [typeValue](#typeValue) “splitting” shall have a single [initial unit versions](#initialUnitVersions) (the unit to split), and at least two [final](#finalUnitVersions) ones (the units resulting from the splitting).


**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)
* [TG DS-SU](./README.md#ref_TG_DS_SU) 5.3.1.2.3.

**Test type**: Automated + Manual

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
reference geometry (VectorStatisticalUnit)<a name="refGeomVSU"></a> | //schema-element(su-vector:VectorStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:geometryType/@xlink:href="http://inspire.ec.europa.eu/codelist/GeometryTypeValue/referenceGeometry" | 1 (1..\* for the parent) | No
GM_MultiSurface (VectorStatisticalUnit)<a name="GM_MultiSurfaceVSU"></a> | //schema-element(su-vector:VectorStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometry/gml:MultiSurface | 1 (1..\* for the parent) | No
reference geometry (AreaStatisticalUnit)<a name="refGeomASU"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:geometryType/@xlink:href="http://inspire.ec.europa.eu/codelist/GeometryTypeValue/referenceGeometry" | 1 (1..\* for the parent) | No
GM_MultiSurface (AreaStatisticalUnit)<a name="GM_MultiSurfaceASU"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometry/gml:MultiSurface | 1 (1..\* for the parent) | No
GM_Surface (AreaStatisticalUnit)<a name="GM_SurfaceASU"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometry/gml:Surface | 1 (1..\* for the parent) | No
mostDetailedScale<a name="mostDetailedScale"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:mostDetailedScale <br> //schema-element(su-vector:VectorStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:mostDetailedScale | 0..1 (1..\* for the parent) | No
leastDetailedScale<a name="leastDetailedScale"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:leastDetailedScale <br> //schema-element(su-vector:VectorStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:leastDetailedScale | 0..1 (1..\* for the parent) | No
Generalised Geometry<a name="generalisedGeometry"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:geometryType/@xlink:href="http://inspire.ec.europa.eu/codelist/GeometryTypeValue/generalisedGeometry" <br> //schema-element(su-vector:VectorStatisticalUnit)/su-vector:geometry/su-vector:VectorStatisticalUnitGeometry/su-vector:geometryDescriptor/su-vector:GeometryDescriptor/su-vector:geometryType/@xlink:href="http://inspire.ec.europa.eu/codelist/GeometryTypeValue/generalisedGeometry" | 1 (1..\* for the parent) | No
typeValue <a name="typeValue"></a> | //schema-element(su-vector:Evolution)/su-vector:evolutionType/@xlink:href | 1 | No
initialUnitVersions <a name ="initialUnitVersions"></a> | //schema-element(su-vector:Evolution)/su-vector:initialUnitVersions/@xlink:href | 0..\* | Yes
finalUnitVersions <a name ="finalUnitVersions"></a> | //schema-element(su-vector:Evolution)/su-vector:finalUnitVersions/@xlink:href | 0..\* | Yes
