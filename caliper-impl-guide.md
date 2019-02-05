var t2 = `
## Overview

### What is this document?

This document is an informative part of the 
[Caliper 1.2 document set](https://www.imsglobal.org/example/v1p1/#document-set).
As such, it may be revised without the specification version being incremented.
Please refer to the [revision history](#revision-history) below for more information 
about revisions to this document. 

To review the use case collection that drove the development of this specification, 
please refer to [the use cases section](https://www.imsglobal.org/example/v1p1/#use-cases) 
in [[EXAMPLE10]].

## What is Caliper?

Caliper is a technical specification to help institutions collect learning and usage data from digital resources and learning tools. This can help you present this information to students, instructors, and advisers in meaningful ways.

Caliper defines a common vocabulary for what activities can be observed (via a "Sensor") and how those activities should be described in JSON. These JSON payloads can be sent to an endpoint via a secure HTTP request for processing or storage. 

Some examples of observable activities are how a learner interacts in a forum, while taking an assessment, or when consuming course readings and videos. 

## Links to documents for your convenience

Many documents will be referenced in this guide. Here are links that will be useful for finding help and further information.

- Public Forums
- Full Specification
- Profiles
- Certification stuff
- How to use with LTI document
- Others?


### Conformance



### Terminology

Learning this vocabulary in the context of the Caliper specification will be very helpful when using this document.

<dl>
  <dt>Action</dt><dd>Part of an Event.</dd>
  <dt>Actor</dt><dd>Part of an Event.</dd>
  <dt>Agent</dt><dd></dd>
  <dt>Entity</dt><dd></dd>
  <dt>Envelope</dt><dd></dd>
  <dt>Event</dt><dd>A collection of an Actor, an Action, and an Object</dd>
  <dt>Metric Profile</dt><dd></dd>
  <dt>Object</dt><dd>Part of an Event.</dd>
  <dt>Sensor</dt><dd></dd>
  <dt></dt><dd></dd>
</dl>

Here is a simple explanation of how Caliper works using this vocabulary. If you can understand this you're well on your way to understanding Caliper!

When a Caliper-observable interaction, as defined by a _Metric Profile_, is detected by a _Sensor_, an _Event_ is created which consists of an _Actor_, an _Object_, and an _Action_. (The Actor did the Action to the Object) To emit an _Event_ to another system via an API call, it is described as a JSON object which is wrapped in an _Envelope_ with a little metadata about the _Sensor_. The JSON is then sent via a secured HTTP call with an authentication token in an HTTP header.

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
- Do _not_ rely on it for grades! Use: list other standards & services?
_ Do not rely on it for course and enrollment information. Use: list other standards & services? 



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
