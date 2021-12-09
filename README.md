# Define-LD
Linked Data Schema for Clinical Trial Datasets. CDISC-compliant submission metadata using JSON-LD.

# Motivation
_The Clinical Research community are passionate about data and metadata standards, which is why we have so many._

[FAIR](https://www.nature.com/articles/sdata201618) data approaches are essential for effective research and automation of Clinical Trial submissions.

The CDISC submission standards are mandatory but are often not considered to the needs of research organisations, who need:
* Human-readability, intuitive links
* Control of the standards for compatibility with their own systems
* A more accessible format than SAS datasets and .XML metadata files

This has led to silo-ing, with individual departments within each company building their own walled garden of standards and process.

An ironic side-effect of this is the proliferation of yet more standards and complexity when initiatives try to bridge the gap - **this project must remain mindful of this hypocrisy.**

By building a JSON-LD representation of the mandatory metadata standard we can leverage its structure in a way that works natively with APIs and semantic clinical data ontologies without the need for additional transformation steps.

# How it works
Data in any form is self-descriptive via tags for its `@id` and a `@context`, a URL linking it back to its study metadata API endpoint.

An `@id` is typically an easily-understood short name can form a longer [IRI](https://www.w3.org/TR/ld-glossary/#internationalized-resource-identifier) when looking up its meaning against the provided `@context`.

The study metadata definition itself is the endpoint of the data `@context`, providing metadata specific to the study that the data belongs to. The study metadata definition includes e.g. datasets, variables, controlled terms, Biomedical Concepts (a combination of domain, variable and value-level metadata breakdown) used by the study.

The study-specific metadata definition is also JSON-LD format and contains a `@schema` linking to a master version of the `Define-LD` schema definition. 

All studies with metadata following `Define-LD` schema link effectively form a distributed MDR with interoperability between CDISC structure and semantic ontologies while keeping the contributing files small and targeted.
