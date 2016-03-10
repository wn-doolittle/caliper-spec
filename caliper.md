### Caliper Analytics<sup>TM</sup> Specification, version 1.1
### IMS Global Learning Consortium, Inc.

### Table of Contents
* 1.0. [Introduction](#introduction)
* 1.x. [Namespaces](#namespaces)
* 1.x. [Definitions](#definitions)
* 1.x. [Terminology](#terminology)
* 2.x. [Data and Semantic Interoperability](#interoperability)
* X.0. [Event](#event)
* X.0. [Entity](#entity)
* X.0. [Profiles](#profiles)
* X.x. [Contributors](#contributors)
*	[Appendix A: Caliper Actions](#appendixA)
* [Appendix B: Caliper Entities](#appendixB)
* [References](#references)


<a name="introduction"/>  
### 1.0. Introduction

TODO

<a name="namespaces"/>  
### 1.x. Namespaces

The Caliper information model references a number of terms derived from other ontologies.  Such terms along with those native to Caliper are identified with a prefix drawn from the list below that maps to the relevant namespace as, for example, the data type [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime).

| Prefix | Namespace | Description |
| ------ | --------- | ----------- |
| clpr | http://purl.imsglobal.org/caliper/v1/ | Caliper |
| clpract | http://purl.imsglobal.org/vocab/caliper/v1/action# | Caliper actions |
| clprlis | http://purl.imsglobal.org/caliper/v1/lis/ | Caliper LIS |
| clprw3c | http://purl.imsglobal.org/caliper/v1/w3c/ | Caliper W3C |
| dc | http://purl.org/dc/elements/1.1/	| Dublin Core Elements |
| dcterms |	http://purl.org/dc/terms/	| Dublin Core Terms |
| dcmitype |	http://purl.org/dc/dcmitype/	| Dublin Core Type Vocabulary |
| foaf | http://xmlns.com/foaf/spec/#	| Friend-of-a-Friend Vocabulary |
| oa |	http://www.w3.org/ns/oa#	| The Open Annotation ontology |
| prov |	http://www.w3.org/ns/prov#	| Provenance Ontology |
| provo | http://www.w3.org/TR/2013/REC-prov-o-20130430/# | PROV-O: the PROV Ontology |
| rdf |	http://www.w3.org/1999/02/22-rdf-syntax-ns#	| RDF |
| rdfs |	http://www.w3.org/2000/01/rdf-schema#	| RDF Schema |
| sdo | http://schema.org/ | schema.org |
| skos |	http://www.w3.org/2004/02/skos/core# | Simple Knowledge Organization System |
| xsd | https://www.w3.org/TR/xmlschema11-2/# | XML Schema Definition Language 1.1 |

### 1.x. Key words

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](#rfc2119).

<a name="definitions"/>  
### 1.x. Definitions

__actor__: TODO

__action__: TODO

__blank node__: A locally-scoped identifier that is used to refer to a resource when a globally scoped identifier is either inappropriate, as in the case of transient data, or not provided.  A blank node is prefixed with an underscore (_) and is scoped to the document in which it is used (e.g., _:a1).

__context__: TODO

__endpoint__: TODO

__entity__: TODO

__event__: TODO

__JSON-LD__: TODO

__LTI__: TODO

__IRI__: The Internationalized Resource Identifier (IRI) extends the Uniform Resource Identifier (URI) scheme by using characters drawn from the Universal Character Set rather than ASCII.  The IRI is a globally scoped identifier used in linked data to refer to most nodes and properties.  An IRI reference may be absolute or relative to that of another absolute IRI.  In JSON-LD relative IRIs are resolved relative to the base IRI.

__ISO 8601__: Caliper time values are formatted per ISO 8601 with the addition of millisecond precision.  The format is yyyy-MM-ddTHH:mm:ss.SSSZ where 'T' separates the date from the time while 'Z' indicates that the time is in UTC. 

__profile__: TODO

__sensor__: TODO

<a name="interoperability">
### 2.0 Data and Semantic Interoperability

TODO

<a name="event"/>
### X.0. Event

__Node type:__ [http://purl.imsglobal.org/caliper/v1/Event](http://purl.imsglobal.org/caliper/v1/Event)

__Comment:__ a Caliper [Event](#event) is a generic class that represents the interaction between an [actor](#actor) and an [object](#actor) at a specific moment in time within the bounds of a specified context. For enhanced specificity implementors SHOULD utilize the several subclasses of [Event](#event) when constructing aN [Event](#event) rather than instantiating instances of the [Event](#event) class itself.

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | -----------: |
| @context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD context represented by a globally-scoped IRI. | 1 |
| @type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD type represented as a globally-scoped IRI. | 1 |
| actor | [clpr:Agent](#agent) | The [Agent](#agent) who initiated or is the subject of the [Event](#event), typically a [Person]([#person), [Organization]([#organization) or [SoftwareApplication]([#softwareapplication). | 1 |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | . . . | 1 |
| object | [clpr:Entity]([#entity) | . . . | 1 |
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when the [Event](#event) occurred. | 1 |
| target | [clpr:Entity]([#entity) | . . . | 0..1 |
| generated | [clpr:Entity]([#entity) | . . . | 0..1 |
| edApp | [clpr:SoftwareApplication]([#softwareapplication) | . . . | 0..1 |
| group | [clprw3c:Organization]([#organization) | . . . | 0..1 |
| membership | [clprlis:Membership]([#membership) | . . . | 0..1 |
| session | [clpr:Session]([#session) | . . . | 0..1 |

__Requirements:__ 

* An [Event](#event) @context MUST be specified.  TODO 
* An [Event](#event) @type MUST be specified.  TODO
* An [Event](#event) MUST include an [actor](#actor), [action](#action), [object](#object) and an [eventTime](#eventTime).
* An [Event](#event) SHOULD include a [session](#session) if the [Event](#event) is generated as a result of an [LTI](#lti) launch.
* Subclasses of [Event](#event) MAY specify additional properties or recommend inclusion of optional properties for a more concise representation of the [Event](#event).

__Subclasses__

[AnnotationEvent](#annotationEvent), [AssignableEvent](#assignableEvent), [AssignmentEvent](#assignmentEvent), [AssignmentItemEvent](#assignmentItemEvent), [ReadingEvent](#readingEvent), [MediaEvent](#mediaEvent), [NavigationEvent](#navigationEvent), [OutcomeEvent](#outcomeEvent), [SessionEvent](#sessionEvent), [ViewEvent](#viewEvent)

__Example__

```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/ViewEvent",             
  "actor": {
    "@id": "https://example.edu/user/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed",
  "object": {
    "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3)",
    "@type": "http://www.idpf.org/epub/vocab/structure/#volume"
  }
  "eventTime": "2015-09-15T10:15:00.000Z"
}
```

<a name="entity">
### X.0. Entity

__type__: [http://purl.imsglobal.org/caliper/v1/Entity](http://purl.imsglobal.org/caliper/v1/Entity)

__Comment__: a Caliper [Entity](#entity) is a generic class that is analogous to an [sdo:Thing](http://schema.org/Thing).  Given its generic nature it is RECOMMENDED that only subclasses of [Entity](#entity) be employed to represent nodes in the learning graph.  

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | -----------: |
| @context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD context represented by a globally-scoped IRI. | 1 |
| @id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD identifier represented as a globally-scoped IRI or a locally-scoped blank node identifier. | 1 |
| @type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD type represented as a globally-scoped IRI. | 1 |
| name | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A word or phrase by which the [Entity](#entity) is known.  Analogous to [sdo:name](http://schema.org/name). | 0..1 |
| description | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A short representation of the [Entity](#entity) in written form.  Analogous to [sdo:description](http://schema.org/description). | 0..1 |
| extensions | Map&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string), [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt;   | A map of additional key/value properties relevant to the [Entity](#entity). | 0..1 |
| dateCreated | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when the [Entity](#entity) was created or added to a data set.  Analogous to [sdo:dateCreated](http://schema.org/dateCreated). | 0..1 |
| dateModified | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted  date and time expressed with millisecond precision that represents when the [Entity](#entity) was last modified.  Analogous to [sdo:dateModified](http://schema.org/dateModified). | 0..1 |

__Requirements:__ 

* An [Entity](#entity) SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that [Event](#event) data can be linked and shared.  In cases where an IRI is inappropriate, an [Entity](#entity) MUST be assigned a blank node identifier.

__Subclasses__

[Agent](#agent), [Attempt](#attempt), [AudioObject](#audioobject), [Collection](#collection), [DigitalResource](#digitalresource), [Forum](#forum), [ImageObject](#imageobject), [MediaObject](#mediaobject), [Membership](#membership), [Message](#message), [Organization](#organization), [Person](#person), [Thread](#thread), [Session](#session), [SoftwareApplication](#softwareapplication), [VideoObject](#videoobject)

__Example__

```
{
   TODO
}
```

<a name="profiles"/>
### X.0. Profiles

TODO

<a name="contributors"/>
### X.x. Contributors

The following Caliper Working Group participants contributed to the writing of this specification:

| Name | Organization |
| ------ | --------- |
| [Anthony Whyte](http://github.com/arwhyte) | University of Michigan |

<a name="appendixA"/>   
### Appendix A: Caliper Actions

| Label | IRI | WordNet Gloss |
| ------ | --- | ------------- |
| created | [clpract:Created](http://purl.imsglobal.org/vocab/caliper/v1/action#Created) | [create](http://wordnet-rdf.princeton.edu/wn31/201620211-v): make or cause to be or to become |
| deleted | [clpract:Deleted](http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted) | [delete](http://wordnet-rdf.princeton.edu/wn31/201001860-v): wipe out digitally |
| markedAsRead | [clpract:MarkedAsRead](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead) | [mark](http://wordnet-rdf.princeton.edu/wn31/200923709-v): designate as if by a mark, [read](http://wordnet-rdf.princeton.edu/wn31/200626756-v): interpret something that is written or printed |
| markedAsUnread | [clpract:MarkedAsUnread](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread) | inverse of markedAsRead |
| posted | [clpract:Posted](http://purl.imsglobal.org/vocab/caliper/v1/action#Posted) | [post](http://wordnet-rdf.princeton.edu/wn31/201033289-v): to cause to be directed or transmitted to another place |
| removed | [clpract:Removed](http://purl.imsglobal.org/vocab/caliper/v1/action#Removed) | [remove](http://wordnet-rdf.princeton.edu/wn31/200181704-v): remove from sight |
| subscribed | [clpract:Subscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed) | [subscribe](http://wordnet-rdf.princeton.edu/wn31/202214527-v): receive or obtain regularly |
| updated | [clpract:Updated](http://purl.imsglobal.org/vocab/caliper/v1/action#Updated) | [update](http://wordnet-rdf.princeton.edu/wn31/200835207-v): bring up to date; supply with recent information |
| unsubscribed | [clpract:Unsubscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed) | inverse of subscribed |

<a name="appendixB" />
### Appendix B: Caliper Entities

<a name="agent" />
#### Agent

__subClassOf:__ [Entity](#entity)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Agent](http://purl.imsglobal.org/caliper/v1/Agent)

__Comment:__ a Caliper [Agent](#agent) is a generic class that represents an [Entity](#entity) that can initiate or perform an [action](#appendixA).  It is analogous to a [foaf:Agent](http://xmlns.com/foaf/spec/#term_Agent).  Given that [Agent](#agent) represents a generic type it is RECOMMENDED that only subclasses of [Agent](#agent) be used to represent an [Event](#event) [actor](#actor).

__Subclasses:__ [Organization](#organization), [Person](#person), [SoftwareApplication](#softwareapplication)

<a name="organization" />
#### Organization

__subClassOf:__ [Agent](#agent)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/w3c/Organization](http://purl.imsglobal.org/caliper/v1/w3c/Organization)

__Comment:__ a Caliper [Organization](#organization) represents a group of people organized into a community or other social, commercial, educational or political structure.  The group has a common purpose or reason for existence that spans beyond the set of people belonging to it and can act as an [Agent](#agent). An [Organization](#organization) can often be decomposed into a hierarchical structure.  It is analogous to a [w3c:Organization](https://www.w3.org/TR/vocab-org/#class-organization).

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | -----------: |
| subOrganizationOf | [Organization](#organization) | The parent organization of an [Organization](#organization). | 0..1 |

__Requirements__

* [@type](#type) MUST be specified with an IRI value of http://purl.imsglobal.org/caliper/v1/w3c/Organization.

__Example__

```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/colleges/1/departments/2",
  "@type": "http://purl.imsglobal.org/caliper/v1/w3c/Organization",
  "name": "Department of History",
  "subOrganizationOf": {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/colleges/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/w3c/Organization",
    "name": "College of Social Science"
  }
}
```

<a name="person" />
#### Person

__subClassOf:__ [Agent](#agent)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/lis/Person](http://purl.imsglobal.org/caliper/v1/lis/Person)

__Comment:__ a Caliper [Person](#person) represents a human being, alive or deceased, real or imaginary.  It is analogous to a [foaf:Person](http://xmlns.com/foaf/spec/#term_Person).

__Requirements__

* [@type](#type) MUST be specified with an IRI value of http://purl.imsglobal.org/caliper/v1/Person.

__Example__

```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/users/554433",
  "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person",
  "dateCreated": "2015-08-01T06:00:00.000Z"
}
```

<a name="session" />
#### Session

__subClassOf:__ [Entity](#entity)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Session](http://purl.imsglobal.org/caliper/v1/Session)

__Comment:__ a Caliper [Session](#session) represents a Web application user session.  [SessionEvent](../events/sessionevent.md) [loggedIn](#loggedIn) actions generate a [Session](#session).  For SessionEvent [loggedOut](#loggedOut) actions, the [Session](#session) represents the target of the interaction while in the case of a [SessionEvent](../events/sessionevent.md) [timedOut](#timedOut) action, the [Session](#session) constitutes the object of the interaction. 

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | ----------: |
| actor | [Agent](#agent) | The [Agent](#agent) who establishes the [Session](#session).| 1 |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when a Session commenced.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). | 1 |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision that represents when a Session ended or was terminated.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). | 0..1 |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | ISO 8601 formatted total interval of time required to complete the Attempt. | 0..1 |

__Requirements__

* [@type](#type) MUST be specified with an IRI value of http://purl.imsglobal.org/caliper/v1/Session.
* It is RECOMMENDED that a [startedAtTime](#startedAtTime) be provided for a [SessionEvent](#sessionEvent) with an action of [loggedIn](#loggedIn). 
* [startedAtTime](#startedAtTime) MUST conform to the ISO-8601 date and time format with millisecond precision.
* It is RECOMMENDED that a [endedAtTime](#endedAtTime) be provided for a [SessionEvent](#sessionEvent) with an action of [loggedOut](#loggedOut) or [timedOut](#timedOut).  
* [endedAtTime](#endedAtTime) MUST conform to the ISO-8601 date and time format with millisecond precision.
* [duration](#duration) MUST conform to the ISO-8601 duration format.

__Example__

```JSONLD
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/viewer/session-123456789",
  "@type": "http://purl.imsglobal.org/caliper/v1/Session",
  "name": "session-123456789",
  "actor": {
    "@id": "https://example.edu/user/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person",
    "dateCreated": "2015-08-01T06:00:00.000Z"
  },
  "dateCreated": "2015-09-15T10:15:00.000Z",
  "startedAtTime": "2015-09-15T10:15:00.000Z"
}
```

<a name="softwareapplication" />
#### SoftwareApplication

__subClassOf:__ [Agent](#agent)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/SoftwareApplication](http://purl.imsglobal.org/caliper/v1/SoftwareApplication)

__Comment:__ a Caliper [SoftwareApplication](#softwareapplication) represents a computer program, application, module, platform or system.  It is analogous to a [sdo:SoftwareApplication](http://schema.org/SoftwareApplication) or [dcmitype:Software](http://purl.org/dc/dcmitype/Software).

__Requirements__

* [@type](#type) MUST be specified with an IRI value of http://purl.imsglobal.org/caliper/v1/SoftwareApplication.

__Sample JSON-LD__

```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/reader",
  "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
  "name": "ePub reader"
}
```

<a name="reference" />
### References

<a name="json-ld">
__JSON-LD__  W3C.  M. Sporny, D. Longley, G. Kellog, M. Lanthaler, N. Lindström. JSON-LD 1.0. A JSON-based Serialization for Linked Data. 16 January 2014.  URL. https://www.w3.org/TR/json-ld/.

<a name="lti">
__LTI__  TODO

<a name="rfc2119">
__RFC 2119__ IETF.  S. Bradner. "Key words for use in RFCs to Indicate Requirement Levels". March 1997. URL: https://tools.ietf.org/html/rfc2119.