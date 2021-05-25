# Conformance class: Application schema, Statistical Units Grid

Conformance class for the requirements associated with the application schema. 

To be able to test this conformance class, the encoding of the data set must be known, i.e. this is a parameterized conformance class. The XPath expressions used in this test suite assume that the GML encoding is used. If used with the GML encoding this conformance class has an indirect dependency to the conformance class "GML application schemas, Statistical Units".

This conformance class is part of the [INSPIRE Data Specification on Statistical Units](../README.md).

## Standardization target type

INSPIRE spatial data set

## Dependencies

### Direct dependencies

none

### Indirect dependencies

An indirect dependency is another conformance class whose requirements must be met by a related resource.

| Specification | Conformance class | Related resource | Parameters |
| ------------- | ----------------- | ---------------- | ---------- |
| [TG DS-SU](./README.md#ref_TG_DS_SU) | [Application Schema, Statistical Units Base](../su-as/README.md) | INSPIRE spatial data set encoded in GML, Statistical Units features | n/a |
 
## Feature types <a name="feature-types"></a>

The instantiable feature types in the application schema are:

* StatisticalGridCell
* StatisticalGrid


## External document references

The following abbreviations are used in the test text for referring to external documents:

Abbreviation                     | Document name
-------------------------------- | --------------------------------------------------
TG DS-SU <a name="ref_TG_DS_SU"></a>   | [INSPIRE Data Specification on Statistical Units – Technical Guidelines version 3.0](http://inspire.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_SU_v3.0.pdf)
TG DS Template <a name="ref_TG_DS_tmpl"></a>   | [INSPIRE Data Specification Template version 3.0rc3](http://inspire.jrc.ec.europa.eu/documents/Data_Specifications/INSPIRE_DataSpecification_Template_v3.0rc3.pdf)

## Test Cases

| Identifier                                                        | Status   | Test case in [TG DS-SU](#ref_TG_DS_SU)  |
| ----------------------------------------------------------------- | -------- | ------------ |
| [Constraints](./constraints.md)  | Draft  | A.1.6  |


## XML namespace prefixes <a name="namespaces"></a>

The following prefixes are used to refer to the corresponding XML namespaces in all test descriptions:

Prefix         | Namespace
-------------- | -------------------------------------------------
su-grid		   | http://inspire.ec.europa.eu/schemas/su-grid/4.0
base           | http://inspire.ec.europa.eu/schemas/base/3.3
gml            | http://www.opengis.net/gml/3.2
wfs            | http://www.opengis.net/wfs/2.0
xsi            | http://www.w3.org/2001/XMLSchema-instance
xlink          | http://www.w3.org/1999/xlink
xml            | http://www.w3.org/XML/1998/namespace
