# IMS Global Learning Consortium, Inc.

# Caliper JSON-LD Context

JSON-LD documents require inclusion of a *context*, denoted by the `@context` keyword, a property employed to map document 
terms to IRIs.  JSON-LD contexts can be embedded inline or referenced externally in a document.  Inclusion of a JSON-LD 
context provides an economical way for Caliper to communicate document semantics to services interested in consuming 
Caliper event data.

IMS Global provides a remote Caliper 1.2 JSON-LD context document for mapping Caliper terms to IRIs.  Implementers are 
encouraged to familiarize themselves with the term definitions described therein. 

## Branches
* __master__: stable, deployable branch that stores the official release history.  
* __develop__: unstable development branch.  Current work that targets a future release is merged to this branch.

## Tags
Caliper JSON-LD context releases are tagged and versioned MAJOR.MINOR.PATCH\[-label\] (e.g., 1.2.0).  Pre-release tags are indentified with an extensions label (e.g., "1.2.0-RC01").  The [tags](https://github.com/IMSGlobal/caliper-contexts/tags) are stored in this repository.

Copyright &copy; 2018 IMS Global Learning Consortium. All Rights Reserved.