var t2 = `
## Overview

### Introduction

This document is an informative part of the 
[Caliper 1.2 document set](https://www.imsglobal.org/example/v1p1/#document-set).
As such, it may be revised without the specification version being incremented.
Please refer to the [revision history](#revision-history) below for more information 
about revisions to this document. 

To review the use case collection that drove the development of this specification, 
please refer to [the use cases section](https://www.imsglobal.org/example/v1p1/#use-cases) 
in [[EXAMPLE10]].



### Conformance



### Terminology



## Key Concepts



## Use Cases



## Best Practices 

### Robustness expectations

As an _analytics_ specification, Caliper is not generally well suited to other uses that require more robust guarantees around timeliness and completeness. 

Notes of what to cover:
- Caliper is _not_ specified as a messaging or transaction service
- There are no guarantees around delivery timing
- Events in Caliper are _not_ ordered and may come much later, or in batches, etc.
- If two vendors need plan to use events as transaction they should work that out in their vendor agreements
- Other reasons why it might not be a good idea to rely on Caliper for user-facing production problems.



## List of Contributors
The following individuals contributed to the development of this document:

| Contributor | Affiliation |
| :---------- | :---------- |
| Anthony Whyte | University of Michigan |
| Viktor Haag | D2L |
| Linda Feng | Unicon |
| Oxana Jurosevic | Instructure |
| Bracken Mosbacker | IMS Global |
        
## Revision History
      
Release Date | Comments
------------ | -------------
Never 12th, 2019 | The original release of the implementation guide

`;
