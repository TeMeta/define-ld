# Define-LD
CDISC-compliant submission metadata via a common boilerplate metadata repository (MDR) schema.

Extends the CDISC metadata standards for clinical trial submission with linked data via [JSON-LD](https://www.w3.org/TR/json-ld11/)

Work with small, simple, self-descriptive targeted subsets of clinical trial data that are linked to and validated against a single source of metadata truth.

# Motivation
_The Clinical Research community are passionate about data and metadata standards, which is why we have so many._

[FAIR](https://www.nature.com/articles/sdata201618) data approaches are essential for effective research and automation of Clinical Trial submissions.

The [CDISC submission standards](https://www.cdisc.org/standards) are mandatory but are often not considered to fulfill the needs of research organisations, who need:
* Human-readability, intuitive links
* Control of the standards for compatibility with their own systems
* A more accessible format than SAS datasets and .XML metadata files

This has led to silo-ing, with individual departments within each company building their own walled garden of standards and process.

An ironic side-effect of this is the proliferation of yet more standards and complexity when initiatives try to bridge the gap - this project must remain mindful of potential hypocrisy here.

By building a JSON-LD representation of the existing mandatory metadata standard we can leverage its structure in a way that works natively with APIs and semantic clinical data ontologies without the need for additional transformation steps.

# Intended Features & Requirements:

* Open clinical trial metadata/MDR schema
* Cross-compatibility between existing trial data and future trials
* ETL CDISC data to FAIR relational data
* Implicit linking to schema.org entities and types
* Define-LD -> Define.XML / Analysis Results Metadata / Trial Design datasets
* Facilitate construction of regulatory datasets from relational data
* Compatibility with other Open Source tools such CDISC CORE and Admiral

# Links to shared external vocabularies
In addition to compatibility with the CDISC Object Data Model, the following external links are included in define-ld wherever possible. This list is an initial recommendation for interoperability, more can be added as needed.

* schema.org
* clinicaltrials.gov
* LOINC
* MedDRA
* WHO
* NCI


# Internal Links Structure
Each of the following has a @context referring to its parent and can be validated against the metadata description provided by its parent.

- define-ld schema
  - [Trial Metadata (versioned in your MDR)](#trial-metadata)
    - clinical data file

This approach allows automatic validation of the metadata structure itself in addition to the validation of the data against its defined structure in the Trial Metadata.

A clinical data file can therefore be (in any format you prefer) a tiny subset of rows and columns compared to the full CDISC dataset but still be “CDISC compliant”, making this scheme an attractive one for practical clinical data management, apps and analytics

# Trial Metadata
The MDR consists of versioned define-ld trial metadata containing as a minimum
* Trial design metadata
* Dataset descriptions
* Dataset columns and links
* Dataset parameters and their allowed values

Other trial metadata can include and is not limited to:
* Protocol metadata (including amendments)
* Analysis results metadata i.e. descriptions of subsets, tables, plots and dashboards
* External dictionaries and vocabularies
* Mapping from upstream data (this can be according to shared mapping schemes such as Pharmaverse or you can implement your own)


