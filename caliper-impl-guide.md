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

### What is Caliper?

Caliper is a technical specification to help institutions collect learning and usage data from digital resources and learning tools. This can help you present this information to students, instructors, and advisers in meaningful ways.

Caliper defines a common vocabulary for what activities can be observed (via a "Sensor") and how those activities should be described in JSON. These JSON payloads can be sent to an endpoint via a secure HTTP request for processing or storage. 

Some examples of observable activities are how a learner interacts in a forum, while taking an assessment, or when consuming course readings and videos. 

### Links to documents for your convenience

Many documents will be referenced in this guide. Here are links that will be useful for finding help and further information.

- Public Forums
- Full Specification
- Profiles
- Certification stuff
- How to use with LTI document
- Others?


## Conformance



## Terminology

Learning this vocabulary in the context of the Caliper specification will be very helpful when using this document.

TODO: Add definitions, and Figure out what definitions to include here vs leaving to the full spec.

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

Here is a short explanation of how Caliper works using this vocabulary. If you can understand this you're well on your way to understanding Caliper!

When a Caliper-observable interaction, as defined by a _Metric Profile_, is detected by a _Sensor_, an _Event_ is created which consists of an _Actor_, an _Object_, and an _Action_. (The Actor did the Action to the Object) To emit an _Event_ to another system via an API call, it is described as a JSON object which is wrapped in an _Envelope_ with a little metadata about the _Sensor_. The JSON is then sent via a secured HTTP call with an authentication token in an HTTP header.


## How to create a Caliper Event

### Events

TODO: What is an event: An Actor, Action, and Object

#### Event JSON stub

```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:3a648e68-f00d-4c08-aa59-8738e1884f2c",
  "type": "ViewEvent",
  "eventTime": "2018-11-15T10:15:00.000Z",
  "actor": {},
  "action": "",
  "object": {}
}
```

### Actors

TODO: Explain Actors and their basic properties then link to main spec document where appropriate for more details.

#### Actor JSON

```json
{
  "id": "https://example.edu/users/554433",
  "type": "Person"
}
```

### Action

TODO: Explain Actions and their basic properties then link to main spec document where appropriate for more details.

#### Action JSON

```json
"Viewed"
```

### Object

TODO: Explain Objects and their basic properties then link to main spec document where appropriate for more details.

#### Object JSON

```json
{
  "id": "https://example.edu/terms/201801/courses/7/sections/1/readings/1",
  "type": "DigitalResource",
  "name": "Chapter 1 reading"
}
```

### Complete Event Example JSON

To bring it all together, and Event would look something like this:

#### Complete JSON

```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:a2f41f9c-d57d-4400-b3fe-716b9026334e",
  "type": "ViewEvent",
  "eventTime": "2018-11-15T10:16:00.000Z",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Viewed",
  "object": {
    "id": "https://example.edu/terms/201801/courses/7/sections/1/readings/1",
    "type": "DigitalResource",
    "name": "Chapter 1 reading"
  }
}
```

This Event is read as something like: "This Person Viewed this DigitalResource at this eventTime"

#### Smaller, ID-Only JSON

TODO: Short explanation about using ID only (or "Type Coercion") instead of full object and then _link_ to more in-depth explanations around proper use. Maybe make a best practice section about when you should generally use object vs just ID and how it needs to be agreed upon between the parties so that they remain interoperable?

```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "id": "urn:uuid:a2f41f9c-d57d-4400-b3fe-716b9026334e",
  "type": "ForumEvent",
  "eventTime": "2018-11-15T10:16:00.000Z",
  "actor": "https://example.edu/users/554433",
  "action": "Subscribed",
  "object": "https://example.edu/terms/201801/courses/7/sections/1/forums/1"
}
```

### Additional properties on Events

While the base information required by most Events is represented in the above example, each Event type could require more properties, and allow for more properties and context as desired by the implementors. To understand what information is required and possible you should consult the Metric Profiles for the activities you're trying to implement.

## Metric Profiles

TODO: Profiles are so amazing!

A great way to think of a Metric Profile is by the questions it can help answer. For example the Reading Profile could help Instructors and researchers answer questions such as:

 - Who is consuming the content?
 - What materials are being accessed?
 - When are the resources accessed?
 - How often is the content viewed?
 - What paths are taken to reach the content?
 

Talk about how `@context` changes for extensions and explain how it works? Then point to the Release Schedule section. 
 
 
## Custom Extensions

TODO: how to do this. Don't know where best to put this section. Might be mostly pointing to other JSON-LD resources.


## Sending an Event to an endpoint

### Envelopes

TODO: Talk about Envelopes and give example. (are Envelopes best discussed in a different section?)

An Envelope must have the properties

#### Base Envelope JSON

```json
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2018-11-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": []
}
```

TODO: Talk about what can be in data: just an event, multiple events, or even mixed payloads of objects and events.

#### Envelope with an Event JSON

```json
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2018-11-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": [{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "urn:uuid:7e10e4f3-a0d8-4430-95bd-783ffae4d916",
    "type": "ToolUseEvent",
    "eventTime": "2018-11-15T10:15:00.000Z",
    "actor": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "action": "Used",
    "object": {
      "id": "https://example.edu",
      "type": "SoftwareApplication"
    }
  }]
}
```

#### Mixed payload Envelope JSON

In this example, the Person and SoftwareApplication are part of the data array and referenced from the events for reuse.

```json
{
  "sensor": "https://example.edu/sensors/1",
  "sendTime": "2018-11-15T11:05:01.000Z",
  "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p2",
  "data": [
   {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "https://example.edu/users/554433",
    "type": "Person",
    "dateCreated": "2018-08-01T06:00:00.000Z",
    "dateModified": "2018-09-02T11:30:00.000Z"
  },
  {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "urn:uuid:7e10e4f3-a0d8-4430-95bd-783ffae4d916",
    "type": "ToolUseEvent",
    "eventTime": "2018-11-15T10:15:00.000Z",
    "actor": "https://example.edu/users/554433",
    "action": "Used",
    "object": "https://example.edu"
  },
  {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p2",
    "id": "urn:uuid:9r34jdfj-a0d8-4430-95bd-783ffae4d916",
    "type": "ToolUseEvent",
    "eventTime": "2018-11-15T11:15:00.000Z",
    "actor": "https://example.edu/users/554433",
    "action": "Used",
    "object": "https://example.edu"
  }
  ]
}
```



### Sending to a secured HTTP endpoint

TODO: Short description of how it's done then link to the LTI service definition: https://github.com/IMSGlobal/LTI-spec-Caliper/blob/develop/lti-spec-caliper.md#23-communicating-the-availability-of-the-service

Also explain how 2 vendors can work out keys and endpoints independent of LTI.


## Release Schedule stuff

- Core spec once a year
 - new base context is updated

- Profiles can be extended during year
 - profile is described in core
 - and might be extensions
 - manifested in JSON as a different @context string by adding `-extension`


## Use Cases

TODO: Find some demonstrative use cases and explain how they'd be solved by talking through what questions they want answered, then what Metric Profiles and Events are needed to answer them.

Make sure to get a use case that decides why and how to add custom extensions.

## Best Practices 

TODO: talk with current implementors and ask what best practices they'd suggest.

### Robustness expectations

As an _analytics_ specification, Caliper is not generally well suited to other uses that require more robust guarantees around timeliness and completeness. 

TODO: Notes of what to cover:
- Caliper is _not_ specified as a messaging or transaction service
- There are no guarantees around delivery timing
- Events in Caliper are _not_ ordered and may come much later, or in batches, etc.
- If two vendors need plan to use events as transaction they should work that out in their vendor agreements
- Other reasons why it might not be a good idea to rely on Caliper for user-facing production problems.
- Do _not_ rely on it for grades! Use: list other standards & services?
_ Do not rely on it for course and enrollment information. Use: list other standards & services? 


### Industry Analytics and Data Retention Standards

TODO: Explain and link to industry best practices around ethics, data retention best practices and laws, and other stuff? I assume there are some good resources out there for researchers and IRB training.


### JSON-LD

TODO: The implementation guide probably doesn't need to dive very deeply into JSON-LD, so give some notes about what JSON-LD is and how Caliper uses it then links to Caliper docs and JSON-LD docs for further learning if necessary


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
