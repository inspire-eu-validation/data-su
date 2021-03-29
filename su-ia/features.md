# Feature references

**Purpose**: Verify that referenced features can be retrieved.

**Prerequisites**

**Test method**

* Verify that any feature reference in an association role is publicly accessible via HTTP, i.e. inspect all relevant properties. If a reference (@xlink:href) has a value that starts with "#", verify that an element with a `gml:id` attribute with the referenced identifier exists in the same document. If the reference starts with "http", verify that a HTTP GET request to the URI retrieves an XML document. Otherwise report [brokenLink](#brokenLink).

This data theme currently has the following association role:

* [VectorStatisticalUnit.evolutions](#evolutions): Evolution
* [AreaStatisticalUnit.administrativeUnit](#administrativeUnit): AdministrativeUnit
* [AreaStatisticalUnit.lowers](#lowersASU): AreaStatisticalUnit
* [AreaStatisticalUnit.uppers](#uppersASu): AreaStatisticalUnit
* [AreaStatisticalUnit.successors](#successors): AreaStatisticalUnit
* [AreaStatisticalUnit.predecessors](#predecessors): AreaStatisticalUnit
* [AreaStatisticalUnit.tesselation](#tesselation): StatisticalTessellation
* [StatisticalTessellation.units](#unitsST): AreaStatisticalUnit
* [StatisticalTessellation.lower](#lowerST): StatisticalTessellation
* [StatisticalTessellation.upper](#upperST): StatisticalTessellation
* [Evolution.finalUnitVersions](#finalUnitVersions): VectorStatisticalUnit
* [Evolution.units](#unitsE): VectorStatisticalUnit
* [Evolution.initialUnitVersions](#initialUnitVersions): VectorStatisticalUnit

* [StatisticalGridCell.lowers](#lowersSGC): StatisticalGridCell
* [StatisticalGridCell.upper](#upperSGC): StatisticalGridCell
* [StatisticalGridCell.grid](#grid): StatisticalGrid

* [StatisticalGrid.lower](#lowerSG): StatisticalGrid
* [StatisticalGrid.upper](#upperSG): StatisticalGrid
* [StatisticalGrid.cells](#cells): StatisticalGridCell

**Reference(s)**: 

* [TG DS Template](./README.md#ref_TG_DS_tmpl) IR requirement Article 4 (2)

**Test type**: Automated

**Notes**

## Messages

Identifier  |  Message text (parameters start with '$')
---------------------------------------------------------- | -------------------------------------------------------------------------
brokenLink <a name="brokenLink"/>  |  XML document '$filename', $featureType '$gmlid': The property '$propertyName' has a value '$value' that cannot be retrieved using HTTP. Every code list value must be made available in an online registry. 

## Contextual XPath references

The namespace prefixes used as described in [README](./README.md#namespaces).

Abbreviation                         |  XPath expression    | Multiplicity    | Voidable
------------------------------------ | ---------------------|-----------------|------------
VectorStatisticalUnit.evolutions <a name ="evolutions"></a>	| //schema-element(su-vector:VectorStatisticalUnit)/su-vector:evolutions/@xlink:href | 0..\* | Yes
AreaStatisticalUnit.administrativeUnit <a name ="administrativeUnit"></a>	| //schema-element(su-vector:AreaStatisticalUnit)/su-vector:administrativeUnit/@xlink:href | 0..\* | Yes
AreaStatisticalUnit.lowers <a name ="lowersASU"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:lowers/@xlink:href | 0..\* | Yes
AreaStatisticalUnit.uppers <a name ="uppersASu"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:uppers/@xlink:href | 0..\* | Yes
AreaStatisticalUnit.successors <a name ="successors"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:successors/@xlink:href | 0..\* | Yes
AreaStatisticalUnit.predecessors <a name ="predecessors"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:predecessors/@xlink:href | 0..\* | Yes
AreaStatisticalUnit.tesselation <a name ="tesselation"></a> | //schema-element(su-vector:AreaStatisticalUnit)/su-vector:tesselation/@xlink:href | 0..1 | Yes
StatisticalTessellation.units <a name ="unitsST"></a> | //schema-element(su-vector:StatisticalTessellation)/su-vector:units/@xlink:href | 0..\* | Yes
StatisticalTessellation.lower <a name ="lowerST"></a> | //schema-element(su-vector:StatisticalTessellation)/su-vector:lower/@xlink:href | 0..1 | Yes
StatisticalTessellation.upper <a name ="upperST"></a> | //schema-element(su-vector:StatisticalTessellation)/su-vector:upper/@xlink:href | 0..1 | Yes
Evolution.finalUnitVersions <a name ="finalUnitVersions"></a> | //schema-element(su-vector:Evolution)/su-vector:finalUnitVersions/@xlink:href | 0..\* | Yes
Evolution.initialUnitVersions <a name ="initialUnitVersions"></a> | //schema-element(su-vector:Evolution)/su-vector:initialUnitVersions/@xlink:href | 0..\* | Yes
Evolution.units <a name ="unitsE"></a> | //schema-element(su-vector:Evolution)/su-vector:units/@xlink:href | 1..\* | Yes
StatisticalGridCell.lowers <a name ="lowersSGC"></a> | //schema-element(su-grid:StatisticalGridCell)/su-grid:lowers/@xlink:href | 0..\* | Yes
StatisticalGridCell.upper <a name ="upperSGC"></a> | //schema-element(su-grid:StatisticalGridCell)/su-grid:upper/@xlink:href | 0..1 | Yes
StatisticalGridCell.grid <a name ="grid"></a> | //schema-element(su-grid:StatisticalGridCell)/su-grid:grid/@xlink:href | 1 | No
StatisticalGrid.lower <a name ="lowerSG"></a> | //schema-element(su-grid:StatisticalGrid)/su-grid:lower/@xlink:href | 0..1 | Yes
StatisticalGrid.upper <a name ="upperSG"></a> | //schema-element(su-grid:StatisticalGrid)/su-grid:upper/@xlink:href | 0..1 | Yes
StatisticalGrid.cells <a name ="cells"></a> | //schema-element(su-grid:StatisticalGrid)/su-grid:cells/@xlink:href | 1..\* | No
