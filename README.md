# DOB: Open Built Environment Data (Draft)

![Correct TTL format](https://github.com/abc-rp/dob/actions/workflows/ttlformat.yaml/badge.svg)

**IMPORTANT:** This document is a draft and is subject to change.

## Introduction

DOB is an initiative that provides structured open data for the built environment, enabling data sharing and connectivity.  
The platform is built on the principles of Linked Data, ensuring that the data can be easily connected with other data sources on the web.  
This enables the creation of a network of built environment data that can be used in a wide range of applications.

## The DOB Ontology

The draft DOB ontology documentation can be found [here](docs/ontology.md).  
The documentation provides an overview of the core vocabulary and property definitions used in the DOB platform as well as how they interact with existing established ontologies.

## Persistent Identifier

We use the w3id.org service to provide a persistent identifier for the DOB platform.  
This identifier will be used to reference all vocabularies, instance identifiers, and linked data resources related to the DOB platform:

```
https://w3id.org/dob
```

Using a persistent identifier ensures long-term stability and makes it easier to reference DOB resources across the web.

## Prefixes

The following prefixes will be used to distinguish between vocabularies and instance IDs.

| Prefix | URI | Description | Licence |
|--------|-----|-------------|---------|
| **dob** | `https://w3id.org/dob/voc#` | Core DOB vocabulary. Example usage: `dob:Result` | Proposed: `CC-BY` |
| **dop** | `https://w3id.org/dob/voc/prop#` | Property definitions. Example usage: `dop:Height` | Proposed: `CC-BY` |
| **bng** | `https://w3id.org/dob/voc/epsg-27700#` | British National Grid vocabulary. Example usage: `bng:easting` | Proposed: `CC-BY` |
| **did** | `https://w3id.org/dob/id/` | Instance Identifiers. Example usage: `did:zone_12345` | Proposed: Various (see [Named Graphs](#named-graphs)) |

## Named Graphs

Data in the DOB platform will be organised into named graphs to enhance performance and to handle licensing requirements.  
These graphs will ensure that specific datasets or themes can be managed separately.

### Base Namespace

The base namespace for DOB graphs is:

```
https://w3id.org/dob/graph/
```

This serves as the foundation for all named graphs under the DOB platform.

### Ontology Namespace

All ontologies used in the DOB platform will be placed in their own graph for ease of reuse across other named graphs.

```
https://w3id.org/dob/graph/ontology/
```

#### Licence

All DOB ontologies will be released under the `CC-BY` licence, ensuring they can be freely reused.  
Any third-party ontologies included will retain their original licences and will be documented in this graph.

### Domain-Specific Insights

The DOB platform will facilitate insights for specific domains of interest (e.g., built environment, economy, health).  
Each theme will have its own named graph, and location-specific data will be partitioned by country using ISO 3166-1 country codes (e.g., `gb/`, `us/`).

For example, insights related to the built environment in the United Kingdom will be stored in the following graph:

```
https://w3id.org/dob/graph/built-environment/gb/
```

#### Licence

Data published under domain-specific insights will be licensed as `ODbL + CC-BY-SA` to encourage openness and ensure that contributions remain open for further development by the community.

### National Alignment

DOB uses a consistent naming convention to create instance identifiers, where the class type is prefixed to a UUID (e.g., `did:zone_9a7478fa-9505-4f67-9406-1592586c9232`).  
This allows unique identification of entities such as zones across different geographies.

However, many locations have their own naming conventions, and it's essential to link DOB’s identifiers to existing datasets for better interoperability.

For example, in the UK, every building is assigned a UPRN (Unique Property Reference Number), and super output areas are widely used in other linked data repositories.  
We will create alignment graphs to link our unique zone IDs to these existing datasets.

The graph for UK zone alignment would be:

```
https://w3id.org/dob/graph/built-environment/gb/zones/
```

This allows users to connect DOB’s unique zone identifiers to existing datasets such as the UPRN database.

#### Licence

Where possible, DOB will publish alignment data under open licences like `CC-BY` to facilitate reuse.  
If source data has specific licensing requirements (e.g., OS UPRN data using `OGL-UK-3.0`), these licences will be reflected in the alignment graph licence.

## Feedback and Contributions

Please submit any feedback, suggestions, or issues through our GitHub issue tracker. Contributions are welcome as we improve the design.

### How to Contribute

**NOTE:** No pull request will be accepted or reviewed until all ttl files in the repository are passing the correct formatting test.

#### 1. Reporting Issues
If you find a bug, inconsistency, or have suggestions for improvements, please open an issue in our [GitHub issue tracker](https://github.com/abc-rp/dob/issues).

When submitting an issue:
- Provide a clear and concise description of the problem.
- If possible suggest potential solutions or improvements.

#### 2. Contributing to the Ontology
If you want to propose changes or additions to the DOB ontology:
1. **Check for existing discussions**: Review open issues and discussions to see if your suggestion has already been proposed.
2. **Fork the repository**: Create your own copy of the repository to work on.
3. **Make changes**: Edit the [ontology files ttl files](voc/), then make sure the [ontology documentation](docs/resources/ontology.md) is also updated. Diagrams can be found and updated in the [.jam file](docs/resources/dob.jam). Additionally provide some [example](docs/resources/examples/) ttl files for any new classes or properties showing how they relate to the existing ontology.
4. **Submit a pull request**:
   - Ensure that your modifications follow Linked Data best practices.
   - Provide a description of why the change is necessary.
   - Reference any related issues in the pull request description.

A general aim of the DOB ontology is to be as lightweight as possible. Only suggest new classes or properties where no existing ontology (especially bot, prov-o, ssn/sosa, dcterms or dcat) suffice.

#### 3. Improving Documentation
Clear documentation is essential. You can contribute by:
- Fixing typos and improving readability.
- Expanding sections with more details or examples.

To contribute documentation changes:
1. Open an issue or check for existing documentation updates.
2. Fork the repository and edit markdown or ttl files.
3. Submit a pull request.