### Caliper Analytics<sup>TM</sup> Specification, version 1.1
### IMS Global Learning Consortium, Inc.

### IPR and Distribution Notices
Recipients of this document are requested to submit, with their comments, notification of any relevant patent claims or other intellectual property rights of which they may be aware that might be infringed by any implementation of the specification set forth in this document, and to provide supporting documentation.

IMS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on IMS’s procedures with respect to rights in IMS specifications can be found at the IMS Intellectual Property Rights web page: [http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Copyright © 2016 IMS Global Learning Consortium. All Rights Reserved.

Use of this specification to develop products or services is governed by the license with IMS found on the IMS website: [http://www.imsglobal.org/license.html](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Permission is granted to all parties to use excerpts from this document as needed in producing requests for proposals.

The limited permissions granted above are perpetual and will not be revoked by IMS or its successors or assigns.

THIS SPECIFICATION IS BEING OFFERED WITHOUT ANY WARRANTY WHATSOEVER, AND IN PARTICULAR, ANY WARRANTY OF NONINFRINGEMENT IS EXPRESSLY DISCLAIMED. ANY USE OF THIS SPECIFICATION SHALL BE MADE ENTIRELY AT THE IMPLEMENTER'S OWN RISK, AND NEITHER THE CONSORTIUM, NOR ANY OF ITS MEMBERS OR SUBMITTERS, SHALL HAVE ANY LIABILITY WHATSOEVER TO ANY IMPLEMENTER OR THIRD PARTY FOR ANY DAMAGES OF ANY NATURE WHATSOEVER, DIRECTLY OR INDIRECTLY, ARISING FROM THE USE OF THIS SPECIFICATION.

### Table of Contents 
* 1.0. [Introduction](#introduction) 
  * 1.x. [Namespaces](#namespaces) 
  * 1.x. [Definitions](#definitions) 
  * 1.x. [Terminology](#terminology)
* 2.0. [Data and Semantic Interoperability](#interoperability) 
* 3.0. [Information Model](#infomodel)  
  * 3.1. [Event](#event) 
  * 3.2. [Entity](#entity) 
  * 3.3. [Profiles](#profiles) 
    * 3.3.1. [Free Form Profile](#freeFormProfile)
    * 3.3.2. [Annotation Profile](#annotationProfile) 
      * 3.3.2.1 [AnnotationEvent](#annotationEvent) 
    * 3.3.3. [Assignable Profile](#assignableProfile)
      * 3.3.3.1 [AssignableEvent](#assignableEvent) 
    * 3.3.4. [Assessment Profile](#assessmentProfile)
      * 3.3.4.1. [AssessmentEvent](#assessmentEvent)
    * 3.3.5. [AssessmentItem Profile](#assessmentItemProfile) 
      * 3.3.5.1. [AssessmentItemEvent](#assessmentItemEvent)
    * 3.3.6. [Discussion Forum Profile](#discussionForumProfile) 
      * 3.3.6.1. [ForumEvent](#ForumEvent) 
      * 3.3.6.2. [ThreadEvent](#ThreadEvent) 
      * 3.3.6.3. [MessageEvent](#messageEvent) 
    * 3.3.7. [Media Profile](#mediaProfile) 
      * 3.3.7.1. [MediaEvent](#mediaEvent) 
    * 3.3.8. [Navigation Profile](#navigationProfile) TODO APPROVE 
      * 3.3.8.1 [NavigationEvent](#navigationEvent) 
    * 3.3.9. [Outcome Profile](#outcomeProfile) 
      * 3.3.9.1 [OutcomeEvent](#outcomeEvent) 
    * 3.3.10. [Reading Profile](#readingProfile) 
      * 3.3.10.1 [ViewEvent](#viewEvent) 
    * 3.3.11. [Session Profile](#sessionProfile) 
      * 3.3.11.1. [SessionEvent](#sessionEvent)
  * 4.0. [Sensor API](#api) 
  * 5.0. [Transport](#transport) 
    * 5.x.x. [Envelope](#envelope) 
  * 6.0. [Endpoints](#endpoints)
  * 7.x. [Contributors](#contributors) 
  *	[Appendix A: Caliper Actions](#appendixA)
  * [Appendix B: Caliper Entities](#appendixB)
  * [References](#references) 
  * [Revision History](#revisionHistory)

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

### 1.x. Terminology
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](#rfc2119).  A Sensor implementation that fails to implement a MUST/REQUIRED/SHALL requirement or fails to abide by a MUST NOT/SHALL NOT prohibition is considered non-conformant.  SHOULD/SHOULD NOT/RECOMMENDED statements constitute a best practice.  Ignoring a best practice does not violate conformance but a decision to disregard such guidance should be carefully considered.  MAY/OPTIONAL statements indicate that implementors are entirely free to choose whether or not to implement the option.

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

<a name="infoModel">
### 3.0 Information Model

TODO

<a name="event"/>
### 3.1. Event
__&#64;type__: [http://purl.imsglobal.org/caliper/v1/Event](http://purl.imsglobal.org/caliper/v1/Event)

__Comment:__ a Caliper [Event](#event) is a generic class that represents the interaction between an [actor](#actor) and an [object](#actor) at a specific moment in time within the bounds of a specified context. For enhanced specificity implementors SHOULD utilize the several subclasses of [Event](#event) when constructing an [Event](#event) rather than instantiating instances of the [Event](#event) class itself.

__Properties__
| Property | Type | Description ||
| -------- | ---- | ----------- | -----------: |
| @context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD context represented by a globally-scoped IRI. | 1 |
| @type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD type represented as a globally-scoped IRI. | 1 |
| actor | [Agent](#agent) | The [Agent](#agent) who initiated or is the subject of the [Event](#event), typically a [Person]([#person), [Organization]([#organization) or [SoftwareApplication]([#softwareapplication). | 1 |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | . . . | 1 |
| object | [Entity]([#entity) | . . . | 1 |
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when the [Event](#event) occurred. | 1 |
| target | [Entity]([#entity) | . . . | 0..1 |
| generated | [Entity]([#entity) | . . . | 0..1 |
| edApp | [SoftwareApplication]([#softwareapplication) | . . . | 0..1 |
| group | [Organization]([#organization) | . . . | 0..1 |
| membership | [Membership]([#membership) | . . . | 0..1 |
| session | [Session]([#session) | . . . | 0..1 |

__Requirements:__ 
* An Event @context MUST be specified.  TODO ELABORATE 
* An Event @type MUST be specified.  TODO ELABORATE
* If a generic Event is created instead of one of its subclasses, the Event [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Event.
* An Event MUST include an [actor](#actor), [action](#action), [object](#object) and an [eventTime](#eventTime).
* An Event [eventTime](#eventTime) value MUST conform to the ISO-8601 date and time format with millisecond precision.
* An Event SHOULD include a [session](#session) if the [Event](#event) is generated as a result of an [LTI](#lti) launch.
* Event properties with a value of null or empty SHOULD be excluded from the JSON-LD representation of the Event.
* Subclasses of Event MAY specify additional properties or RECOMMEND inclusion of optional properties for a more concise representation of the Event.

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
### 3.2. Entity
__&#64;type__: [http://purl.imsglobal.org/caliper/v1/Entity](http://purl.imsglobal.org/caliper/v1/Entity)

__Comment__: a Caliper [Entity](#entity) is a generic class that is analogous to an [sdo:Thing](http://schema.org/Thing).  

__Properties__
| Property | Type | Description ||
| -------- | ---- | ----------- | -----------: |
| @context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD context represented by a globally-scoped IRI. | 1 |
| @id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD identifier represented as a globally-scoped IRI or a locally-scoped blank node identifier. | 1 |
| @type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD type represented as a globally-scoped IRI. | 1 |
| name | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A word or phrase by which the [Entity](#entity) is known.  Analogous to [sdo:name](http://schema.org/name). | 0..1 |
| description | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A short representation of the [Entity](#entity) in written form.  Analogous to [sdo:description](http://schema.org/description). | 0..1 |
| extensions | Map&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string), [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt; | A map of additional key/value properties relevant to the [Entity](#entity). | 0..1 |
| dateCreated | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when the [Entity](#entity) was created or added to a data set.  Analogous to [sdo:dateCreated](http://schema.org/dateCreated). | 0..1 |
| dateModified | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted  date and time expressed with millisecond precision that represents when the [Entity](#entity) was last modified.  Analogous to [sdo:dateModified](http://schema.org/dateModified). | 0..1 |

__Requirements:__ 
* Given that Entity represents a generic type it is RECOMMENDED that only subclasses of [Entity](#entity) be employed to represent nodes in the learning graph.
* An Entity SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that [Event](#event) data can be linked and shared.  In cases where an IRI is inappropriate, an Entity MUST be assigned a blank node identifier.
* If a generic Entity is included in an [Event](#event) instead of one of its subclasses, the Entity [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Entity.
* If an Entity [dateCreated](#dateCreated) is specified, the value MUST conform to the ISO-8601 date and time format with millisecond precision.  
* If an Entity [dateModified](#dateModified) is specified, the value MUST conform to the ISO-8601 date and time format with millisecond precision.

__Subclasses__
[Agent](#agent), [Annotation](#annotation), [Assessment](#assessment), [AssessmentItem](#assessmentItem), [AssignableDigitalResource](#assignableDigitalResource), [Attempt](#attempt), [AudioObject](#audioobject), [BookmarkAnnotation](#bookmarkAnnotation), [Collection](#collection), [CourseOffering](#courseOffering), [CourseSection](#courseSection), [DigitalResource](#digitalresource), [EpubChapter](#epubChapter), [EpubPart](#epubPart), [EpubSubChapter](#epubSubChapter), [EpubVolume](#epubVolume), [FillinBlankResponse](#fillinBlankResponse), [Frame](#frame), [Forum](#forum), [Group](#group), [HighlightAnnotation](#highlightAnnotation), [ImageObject](#imageobject), [LearningObjective](#learningObjective), [MediaLocation](#mediaLocation), [MediaObject](#mediaobject), [Membership](#membership), [Message](#message), [MultipleChoiceResponse](#multipleChoiceResponse), [MultipleResponseResponse](#multipleResponseResponse), [Organization](#organization), [Person](#person), [Reading](#reading), [Response](#response), [Result](#result), [SelectTextResponse](#selectTextResponse), [Session](#session), [SharedAnnotation](#sharedAnnotation), [SoftwareApplication](#softwareapplication), [TagAnnotation](#tagAnnotation), [Thread](#thread), [TrueFalseResponse](#trueFalseResponse), [VideoObject](#videoobject), [WebPage](#webpage)

__Example__
```
{
   TODO
}
```

<a name="profiles"/>
### 3.3. Profiles

TODO

<a name="freeFormProfile" />
#### 3.3.1. Free Form Profile

TODO


<a name="annotationProfile" />
#### 3.3.2. Annotation Profile

TODO

<a name="assignableProfile" />
#### 3.3.3. Assignable Profile

TODO

<a name="assessmentProfile" />
#### 3.3.4. Assessment Profile

TODO

<a name="assessmentItemProfile" />
#### 3.3.5. AssessmentItem Profile

TODO

<a name="discussionForumProfile" />
#### 3.3.6. Discussion Forum Profile

TODO

<a name="mediaProfile" />
#### 3.3.7. Media Profile

TODO

<a name="navigationProfile" />
#### 3.3.8. Navigation Profile

TODO NEEDS APPROVAL

<a name="outcomeProfile" />
#### 3.3.9. Outcome Profile

TODO

<a name="readingProfile" />
#### 3.3.10. Reading Profile

TODO

<a name="sessionProfile" />
### 3.3.11. Session Profile
The Caliper Session Profile models activities associated with a user session established by an [actor](#actor) interacting with a [SoftwareApplication](#softwareApplication).  A single [SessionEvent](#sessionEvent) is provided along with a set of supported actions.

__Supported events__: [SessionEvent](#sessionEvent)

__Supported actions__: [loggedIn](#loggedIn), [loggedOut](#loggedOut), [timedOut](#timedOut)

__Required entities__: [Person](#person), [Session](#session), [SoftwareApplication](#softwareApplication)

__Conformance__
* The [loggedIn](#loggedIn) action is a REQUIRED action and MUST be implemented.
* All other Session Profile supported actions are considered OPTIONAL for conformance purposes.

<a name="sessionEvent" />
#### 3.3.11.1. SessionEvent
__&#64;type__: [http://purl.imsglobal.org/caliper/v1/SessionEvent](http://purl.imsglobal.org/caliper/v1/SessionEvent)

__Comment__: TODO

__Requirements__ 
* A SessionEvent [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SessionEvent.
* SessionEvent property values vary between supported actions.  When generating a SessionEvent, the following action/property value matrix MUST be followed.  In addition, all REQUIRED properties MUST be specified while all OPTIONAL properties SHOULD be specified if a value is listed.

| SessionEvent  | loggedIn | loggedOut | timedOut ||
| --------  | -------- | --------- | -------- | ---: |
| actor | [Person](#person) |[Person](#person) | [SoftwareApplication](#softwareApplication) | 1 |
| action | [loggedIn](#loggedIn) | [loggedOut](#loggedOut) | [timedOut](#timedOut) | 1 |
| object | [SoftwareApplication](#softwareApplication) | [SoftwareApplication](#softwareApplication)  | [Session]([#session) | 1 |
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | 1 |
| target | [DigitalResource](#digitalResource) | [Session]([#session) | &nbsp; | 0..1 |
| generated | [Session]([#session) | &nbsp; | &nbsp; | 0..1 |
| edApp | [SoftwareApplication](#softwareApplication) | [SoftwareApplication](#softwareApplication) | [SoftwareApplication](#softwareApplication)| 0..1 |
| group | [Organization]([#organization) | [Organization]([#organization) | [Organization]([#organization) | 0..1 |
| membership | [Membership]([#membership) |  [Membership]([#membership) |  [Membership]([#membership) | 0..1 |
| session | [Session]([#session) | [Session]([#session) | [Session]([#session) | 0..1 | 

<a name="api"/>
### 4.0. Sensor API

TODO

<a name="transport"/>
### 5.0. Transport

TODO

<a name="endpoints"/>
### 6.0. Endpoints

TODO

<a name="contributors"/>
### 7.0. Contributors
The following Caliper Working Group participants contributed to the writing of this specification:

| Name | Organization |
| ------ | --------- |
| [Anthony Whyte](http://github.com/arwhyte) | University of Michigan |

<a name="appendixA"/>   
### Appendix A: Caliper Actions

| Label | IRI | WordNet Gloss |
| ------ | --- | ------------- |
| <a name="created" />created | [clpract:Created](http://purl.imsglobal.org/vocab/caliper/v1/action#Created) | [create](http://wordnet-rdf.princeton.edu/wn31/201620211-v): make or cause to be or to become |
| deleted | [clpract:Deleted](http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted) | [delete](http://wordnet-rdf.princeton.edu/wn31/201001860-v): wipe out digitally |
| <a name="loggedIn" />logged in | [clpract:LoggedIn](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn) | [log in](http://wordnet-rdf.princeton.edu/wn31/202253955-v): enter a computer or software application |
| <a name="loggedIn" />logged out | [clpract:LoggedOut](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut) | [log out](http://wordnet-rdf.princeton.edu/wn31/202254101-v): exit a computer or software application |
| <a name="markedAsRead" />marked as read | [clpract:MarkedAsRead](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead) | [mark](http://wordnet-rdf.princeton.edu/wn31/200923709-v): designate as if by a mark, [read](http://wordnet-rdf.princeton.edu/wn31/200626756-v): interpret something that is written or printed |
| <a name="markedAsUnread" />marked as unread | [clpract:MarkedAsUnread](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread) | inverse of markedAsRead |
| <a name="posted" />posted | [clpract:Posted](http://purl.imsglobal.org/vocab/caliper/v1/action#Posted) | [post](http://wordnet-rdf.princeton.edu/wn31/201033289-v): to cause to be directed or transmitted to another place |
| <a name="removed" />removed | [clpract:Removed](http://purl.imsglobal.org/vocab/caliper/v1/action#Removed) | [remove](http://wordnet-rdf.princeton.edu/wn31/200181704-v): remove from sight |
| <a name="subscribed" />subscribed | [clpract:Subscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed) | [subscribe](http://wordnet-rdf.princeton.edu/wn31/202214527-v): receive or obtain regularly |
| <a name="updated" />updated | [clpract:Updated](http://purl.imsglobal.org/vocab/caliper/v1/action#Updated) | [update](http://wordnet-rdf.princeton.edu/wn31/200835207-v): bring up to date; supply with recent information |
| <a name="unsubscribed" />unsubscribed | [clpract:Unsubscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed) | inverse of subscribed |

<a name="appendixB" />
### Appendix B: Caliper Entities

<a name="agent" />
#### Agent
__subClassOf:__ [Entity](#entity)

__&#64;type__: [http://purl.imsglobal.org/caliper/v1/Agent](http://purl.imsglobal.org/caliper/v1/Agent)

__Comment:__ a Caliper Agent is a generic class that represents an [Entity](#entity) that can initiate or perform an [action](#appendixA).  It is analogous to a [foaf:Agent](http://xmlns.com/foaf/spec/#term_Agent).

__Requirements__
* Given that [Agent](#agent) represents a generic type it is RECOMMENDED that only subclasses of Agent be used to represent an [Event](#event) [actor](#actor).
* If a generic Agent is included in an [Event](#event) instead of one of its subclasses, the Agent [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Agent.

__Subclasses__ 
[Organization](#organization), [Person](#person), [SoftwareApplication](#softwareapplication)

<a name="annotation" />
#### Annotation

TODO

__Example__
```
{

 TODO
 
}
```

<a name="assessment" />
#### Assessment
__subClassOf:__ [AssignableDigitalResource](#assignableDigitalResource), [Collection](#collection), 

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Assessment](http://purl.imsglobal.org/caliper/v1/Assessment)

__Comment:__ a Caliper Assessment represents . . . TODO.

__Properties__
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| items | List&lt;[AssessmentItem](#assessmentItem)&gt; | The set of items that comprise this Assessment. | 0..1 |

__Requirements__
* An Assessment [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Assessment.

__Example__
```
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
    "name": "Stamp Act Crisis Quiz",
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "dateModified": "2015-09-02T11:30:00.000Z",
    "datePublished": "2015-08-15T09:30:00.000Z",
    "dateToActivate": "2015-08-16T05:00:00.000Z",
    "dateToShow": "2015-08-16T05:00:00.000Z",
    "dateToStartOn": "2015-08-16T05:00:00.000Z",
    "dateToSubmit": "2015-09-28T11:59:59.000Z",
    "maxAttempts": 2,
    "maxScore": 10,
    "maxSubmits": 2,
    "version": "1.0"
}
```

<a name="assessmentItem" />
#### AssessmentItem
__subClassOf:__ [AssignableDigitalResource](#assignableDigitalResource)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Assessment](http://purl.imsglobal.org/caliper/v1/Assessment)

__Comment:__ a Caliper AssessmentItem represents . . . TODO.

__Requirements__
* An AssessmentItem [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssessmentItem.

__Example__
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
  "name": "Assessment Item 1",
  "isPartOf": {
    "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
    "name": "Stamp Act Crisis Quiz",
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "dateModified": "2015-09-02T11:30:00.000Z",
    "datePublished": "2015-08-15T09:30:00.000Z",
    "dateToActivate": "2015-08-16T05:00:00.000Z",
    "dateToShow": "2015-08-16T05:00:00.000Z",
    "dateToStartOn": "2015-08-16T05:00:00.000Z",
    "dateToSubmit": "2015-09-28T11:59:59.000Z",
    "maxAttempts": 2,
    "maxScore": 3.0,
    "maxSubmits": 2,
    "version": "1.0"
  },
  "isTimeDependent": false,
  "maxAttempts": 2,
  "maxScore": 1.0,
  "maxSubmits": 2,
  "version": "1.0"
}
```

<a name="assignableDigitalResource" />
#### AssignableDigitalResource

TODO

__Example__
```
{

 TODO
 
}
```

<a name="attempt" />
#### Attempt

TODO

__Example__
```
{

 TODO
 
}
```

<a name="audioObject" />
#### AudioObject

TODO

__Example__
```
{

 TODO
 
}
```

<a name="bookmarkAnnotation" />
#### BookmarkAnnotation

TODO

__Example__
```
{

 TODO
 
}
```

<a name="collection" />
#### Collection
__subClassOf:__ [Entity](#entity)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Collection](http://purl.imsglobal.org/caliper/v1/Collection)

__Comment:__ a Caliper Collection is a generic class that represents a set of entities.  It is analogous to a [dcmitype:Collection](http://purl.org/dc/dcmitype/Collection) or a [sioc:Container](http://rdfs.org/sioc/spec/#term_Container).  

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| ~~isChildOf~~ | ~~[Collection](#collection)~~ | ~~The parent Collection of this Collection.  Analogous to [sioc:has_parent](http://rdfs.org/sioc/spec/#term_has_parent).~~ | ~~0..1~~ |
| items | List&lt;[Entity](#entity)&gt; | The set of items that comprise this Collection. | 0..1 |

__Requirements__
* Given that a Collection represents a generic type it is RECOMMENDED that only subclasses of Collection be employed to represent nodes in the learning graph.
* If a generic Collection is included in an [Event](#event) instead of one of its subclasses, the Collection [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Collection.

__Subclasses:__ [Assessment](./assessment.md), [Forum](./forum.md), [Thread](./thread.md)

<a name="courseOffering" />
#### CourseOffering

TODO

__Example__
```
{

 TODO
 
}
```

<a name="courseSection" />
#### CourseSection

TODO

__Example__
```
{

 TODO
 
}
```

<a name="digitalResource" />
#### DigitalResource
__subClassOf:__ [Entity](#entity)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/DigitalResource](http://purl.imsglobal.org/caliper/v1/DigitalResource)

__Comment:__ a Caliper DigitalResource is a generic class that represents a content item.  It is analogous to an [sdo:CreativeWork](https://schema.org/CreativeWork).

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | ---: |
| creator | [Agent](#agent) | The [Agent](#agent) responsible for bringing the described DigitalResource into being.  Analogous to [sdo:Creator](http://schema.org/Creator) or [dcterms:creator](http://purl.org/dc/terms/creator). | 0..1 |
| ~~objectType~~ | ~~[xsd:string](https://www.w3.org/TR/xmlschema11-2/#string)~~ | ~~decremented~~| ~~0..1~~ |
| keywords | List&lt;[xsd:string](https://www.w3.org/TR/xmlschema11-2/#string)&gt; | A set of one or more words that are used to tag the content.  Analogous to [sdo:keywords](http://schema.org/keywords) | 0..1 |
| alignedLearningObjective | List&lt;[LearningObjective](#learningobjective)&gt; | One or more [LearningObjectives](#learningobject) that describe what [actor](#actor) is expected to accomplish after engaging with this DigitalResource | 0..1 |
| isPartOf | [DigitalResource](#digitalresource) | A related DigitalResource that includes or incorporates the described DigitalResource as a part of its whole.  Analogous to [sdo:isPartOf](http://schema.org/isPartOf) or [dcterms:isPartOf](http://purl.org/dc/terms/isPartOf). | 0..1 |
| datePublished | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision that represents the publication date of the DigitalResource.  Analogous to [sdo:datePublished](http://schema.org/datePublished) | 0..1 |
| version | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) | An identifier that designates the current form of the DigitalResource.  Analogous to [sdo:version](http://schema.org/version) | 0..1 |

__Requirements__
* Given that DigitalResource represents a generic type it is RECOMMENDED that only its subclasses be employed to represent nodes in the learning graph.
* If a generic DigitalResource is included in an [Event](#event) instead of one of its subclasses, the DigitalResource [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/DigitalResource. 
* If a DigitalResource [datePublished](#datePublished) is specified, the value MUST conform to the ISO-8601 date and time format with millisecond precision.

__Subclasses__
[Assessment](#assessment), [AssessmentItem](#assessmentItem), [AssignableDigitalResource](#assignableDigitalResource), [AudioObject](#audioobject), [DigitalResource](#digitalresource), [EpubChapter](#epubChapter), [EpubPart](#epubPart), [EpubSubChapter](#epubSubChapter), [EpubVolume](#epubVolume), [Frame](#frame), [ImageObject](#imageobject), [MediaLocation](#mediaLocation), [MediaObject](#mediaobject), [Message](#message), [Reading](#reading), [Thread](#thread), [VideoObject](#videoobject), [WebPage](#webpage)

<a name="epubChapter" />
#### EpubChapter

TODO

__Example__
```
{

 TODO
 
}
```

<a name="epubPart" />
#### EpubPart

TODO

__Example__
```
{

 TODO
 
}
```

<a name="epubSubChapter" />
#### EpubSubChapter

TODO

__Example__
```
{

 TODO
 
}
```

<a name="epubVolume" />
#### EpubVolume

TODO

__Example__
```
{

 TODO
 
}
```

<a name="fillinBlankResponse" />
#### FillinBlankResponse

TODO

__Example__
```
{

 TODO
 
}
```

<a name="frame" />
#### Frame

TODO

__Example__
```
{

 TODO
 
}
```

<a name="forum" />
#### Forum
__subClassOf:__ [Collection](#collection)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Forum](http://purl.imsglobal.org/caliper/v1/Forum)

__Comment:__ a Caliper Forum is a channel or virtual space in which group discussions take place.  A Forum typically comprises one or more threaded discussions to which members can subscribe, post messages and reply to other messages.  It is analogous to a [sioc:Forum](http://rfds.org/sioc/spec/#term_Forum).

__Properties__
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| items | List&lt;[Thread](#thread)&gt; | The set of items that comprise this Forum. | 0..1 |

__Requirements__
* A Forum [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Forum.

__Example__
```
{

 TODO
 
}
```

<a name="group" />
#### Group

TODO

__Example__
```
{

 TODO
 
}
```

<a name="highlightAnnotation" />
#### HighlightAnnotation

TODO

__Example__
```
{

 TODO
 
}
```

<a name="imageObject" />
#### ImageObject

TODO

__Example__
```
{

 TODO
 
}
```

<a name="learningObjective" />
#### LearningObjective

TODO

__Example__
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/super-media-tool/videos/1225",
  "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
  "name": "American Revolution - Key Figures Video",
  "alignedLearningObjective": [
    {
      "@id": "https://example.edu/courses/5678/assignments/1/learningobjectives/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/LearningObjective",
      "dateCreated": "2015-08-01T06:00:00.000Z"
    }
  ],
  "duration": 1420,
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "dateModified": "2015-09-02T11:30:00.000Z",
  "version": "1.0"
}
```

<a name="mediaLocation" />
#### MediaLocation

TODO

__Example__
```
{

 TODO
 
}
```

<a name="mediaObject" />
#### MediaObject

__subClassOf:__ [DigitalResource](#digitalResource)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/MediaObject](http://purl.imsglobal.org/caliper/v1/MediaObject)

__Comment:__ a Caliper MediaObject represents a generic piece of media content analogous to [sdo:MediaObject](http://schema.org/MediaObject).

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| duration | [xsd:long](https://www.w3.org/TR/xmlschema11-2/#long) | The length of time to completion.  Analogous to [sdo:duration](http://schema.org/duration).  | 0..1 |

__Requirements__
* Given that MediaObject represents a generic type it is RECOMMENDED that only its subclasses be employed to represent nodes in the learning graph.
* If a generic MediaObject is included in an [Event](#event) instead of one of its subclasses, the MediaObject [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MediaObject. 

__Subclasses:__ [AudioObject](#audioObject.md), [ImageObject](#imageObject.md), [VideoObject](#videoObject) 

<a name="membership" />
#### Membership

TODO

__Example__
```
{

 TODO
 
}
```

<a name="message" />
#### Message

__subClassOf:__ [DigitalResource](#digitalResource)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Message](http://purl.imsglobal.org/caliper/v1/Message)

__Comment:__ a Caliper Message is a digital form of written communication sent to a recipient. A series of Messages may constitute a [Thread](#thread) if they share a common subject and are connected by a reply or by date relationships. It is analogous to an [sioc:Post](http://rfds.org/sioc/spec/#term_Post).

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | ---: |
| creator | [Agent](#agent) | The author or originator of this Message, typically a [Person](#person).  Analogous to [sioc:has_creator](http://rdfs.org/sioc/spec/#term_has_creator) or [sdo:creator](http://schema.org/creator). | 0..1|
| replyTo | [Message](#message) | The prior Message, if any, that prompted the posting of this Message in the form of a reply or response.  Analogous to [sioc:reply_of](http://rdfs.org/sioc/spec/#term_reply_of). | 0..1 |
| isPartOf | [Thread](#thread) | The Thread of which this Message forms a part.  Analogous to [sioc:has_creator](http://rdfs.org/sioc/spec/#term_has_creator). | 0..1 |
| content | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) | Plain-text rendering of the content of the Message.  Analogous to [sioc:content](http://rdfs.org/sioc/spec/#content). | 0..1 |
| attachments | List&lt;[DigitalResource](#digitalResource)&gt; | A set of one or more DigitalResources attached to this Message.  Analogous to [sioc:attachment](http://rdfs.org/sioc/spec/#term_attachment). | 0..1 |

__Requirements__
* A Message [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Message.
* A Message SHOULD specify a [creator](#creator).
* A Message SHOULD specify a [replyTo](#replyTo) if the Message represents a response to a previously posted Message.

TODO SHOULD WE CONSIDER CREATING A "BODY" ENTITY FOR Message.content WITH THE FOLLOWING MINIMUM PROPERTIES:
body string
isAbbreviated or isTruncated boolean

__Example__
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/2/courses/1/forums/2/topics/1/messages/2",
  "@type": "http://purl.imsglobal.org/caliper/v1/Message",
  "creator": {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person"
  },
  "replyTo": {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/terms/2/courses/1/forums/2/topics/1/messages/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Message",
    "creator": {
      "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
      "@id": "https://example.edu/users/12345",
      "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person"
    },
    "content": "Do you like Caliper?",
    "dateCreated": "2016-09-02T11:30:00.000Z"
  },
  "isPartOf": {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/terms/2/courses/1/forums/2/topics/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
    "name": "Caliper Happiness Index",
    "creator": {
      "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
      "@id": "https://example.edu/users/56789",
      "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person"
    },
    "isPartOf": {
      "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
      "@id": "https://example.edu/terms/2/courses/1/forums/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
      "name": "Caliper Forum",
      "creator": {
        "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
        "@id": "https://example.edu/users/56789",
        "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person"
      },
      "dateCreated": "2016-09-01T09:28:00.000Z"
    },
    "dateCreated": "2016-09-01T09:30:00.000Z"
  },
  "content": "I love Caliper!",
  "dateCreated": "2016-09-02T11:32:00.000Z"
}
```

<a name="multipleChoiceResponse" />
#### MultipleChoiceResponse

TODO

__Example__
```
{

 TODO
 
}
```

<a name="multipleResponseResponse" />
#### MultipleResponseResponse

TODO

__Example__
```
{

 TODO
 
}
```

<a name="organization" />
#### Organization

__subClassOf:__ [Agent](#agent)

__&#64;type__: [http://purl.imsglobal.org/caliper/v1/w3c/Organization](http://purl.imsglobal.org/caliper/v1/w3c/Organization)

__Comment:__ a Caliper Organization represents a group of people organized into a community or other social, commercial, educational or political structure.  The group has a common purpose or reason for existence that spans beyond the set of people belonging to it and can act as an [Agent](#agent). An Organization can often be decomposed into a hierarchical structure.  It is analogous to a [w3c:Organization](https://www.w3.org/TR/vocab-org/#class-organization).

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- |---: |
| subOrganizationOf | [Organization](#organization) | The parent Organization of this Organization. | 0..1 |

__Requirements__
* An Organization [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/w3c/Organization.

__Subclasses__

[Group](#group)

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

__&#64;type__: [http://purl.imsglobal.org/caliper/v1/lis/Person](http://purl.imsglobal.org/caliper/v1/lis/Person)

__Comment:__ a Caliper Person represents a human being, alive or deceased, real or imaginary.  It is analogous to a [foaf:Person](http://xmlns.com/foaf/spec/#term_Person).

__Requirements__
* A Person [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Person.

__Example__
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/users/554433",
  "@type": "http://purl.imsglobal.org/caliper/v1/lis/Person",
  "dateCreated": "2015-08-01T06:00:00.000Z"
}
```

<a name="reading" />
#### Reading

TODO

__Example__
```
{

 TODO
 
}
```

<a name="response" />
#### Response

TODO

__Example__
```
{

 TODO
 
}
```

<a name="result" />
#### Result

TODO

__Example__
```
{

 TODO
 
}
```

<a name="selectTextResponse" />
#### SelectTextResponse

TODO

__Example__
```
{

 TODO
 
}
```

<a name="session" />
#### Session

__subClassOf:__ [Entity](#entity)

__&#64;type__: [http://purl.imsglobal.org/caliper/v1/Session](http://purl.imsglobal.org/caliper/v1/Session)

__Comment:__ a Caliper Session represents a Web application user session.

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | ---: |
| actor | [Agent](#agent) | The [Agent](#agent) who establishes the Session.| 0..1 |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when a Session commenced.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). | 0..1 |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision that represents when a Session ended or was terminated.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). | 0..1 |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | ISO 8601 formatted total interval of time required to complete the Attempt. | 0..1 |

__Requirements__
* A Session [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Session.
* It is RECOMMENDED that a Session [actor](#actor) be specified.
* A Session [startedAtTime](#startedAtTime) SHOULD be provided for a [SessionEvent](#sessionEvent). 
* If a Session [startedAtTime](#startedAtTime) is specified, the value MUST conform to the ISO-8601 date and time format with millisecond precision.
* It is RECOMMENDED that a Session [endedAtTime](#endedAtTime) be provided for a [SessionEvent](#sessionEvent) with an action of [loggedOut](#loggedOut) or [timedOut](#timedOut).  
* If a Session [endedAtTime](#endedAtTime) is specified, the value MUST conform to the ISO-8601 date and time format with millisecond precision.
* If a Session [duration](#duration) is specified, the value MUST conform to the ISO-8601 duration format.

__Example__
```
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

<a name="sharedAnnotation" />
#### SharedAnnotation

TODO

__Example__
```
{

 TODO
 
}
```

<a name="softwareapplication" />
#### SoftwareApplication

__subClassOf:__ [Agent](#agent)

__&#64;type__: [http://purl.imsglobal.org/caliper/v1/SoftwareApplication](http://purl.imsglobal.org/caliper/v1/SoftwareApplication)

__Comment:__ a Caliper SoftwareApplication represents a computer program, application, module, platform or system.  It is analogous to a [sdo:SoftwareApplication](http://schema.org/SoftwareApplication) or [dcmitype:Software](http://purl.org/dc/dcmitype/Software).

__Requirements__
* A SoftwareApplication [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SoftwareApplication.

__Sample JSON-LD__
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/reader",
  "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
  "name": "ePub reader"
}
```

<a name="tagAnnotation" />
#### TagAnnotation

TODO

__Example__
```
{

 TODO
 
}
```

<a name="thread" />
#### Thread

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/Thread](http://purl.imsglobal.org/caliper/v1/Thread)

__Comment:__ a Caliper Thread represents a series of one or more messages that share a common subject and are connected by a reply or by date relationships. It is analogous to a [sioc:Thread](http://rfds.org/sioc/spec/#term_Thread).

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | ---: |
| isChildOf | [Forum](#forum) | The parent Forum of this Thread.  Analogous to [sioc:has_parent](http://rdfs.org/sioc/spec/#term_has_parent). | 0..1 |
| items | List&lt;[Message](#message)&gt; | The set of items that comprise this Thread. | 0.1 |

__Requirements__
* A Thread [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Thread.

__Example__
```
{

  TODO
  
}
```

<a name="trueFalseResponse" />
#### TrueFalseResponse

TODO

__Example__
```
{

 TODO
 
}
```

<a name="videoObject" />
#### VideoObject
__subClassOf:__ [MediaObject](#mediaobject)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/VideoObject](http://purl.imsglobal.org/caliper/v1/VideoObject)

__Comment:__ a Caliper VideoObject represents a visual recording stored in digital form. It is analogous to [sdo:VideoObject](http://schema.org/VideoObject).

__Requirements__
* A VideoObject [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/VideoObject.

__Example__
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/super-media-tool/videos/1225",
  "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
  "name": "American Revolution - Key Figures Video",
  "duration": 1420,
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "dateModified": "2015-09-02T11:30:00.000Z",
  "version": "1.0"
}
```

<a name="webPage" />
#### WebPage
__subClassOf:__ [DigitalResource](#digitalresource)

__&#64;type:__ [http://purl.imsglobal.org/caliper/v1/WebPage](http://purl.imsglobal.org/caliper/v1/WebPage)

__Comment:__ a Caliper WebPage represents a document suitable for display in a web browser.  It is analogous to a [sdo:WebPage](http://schema.org/WebPage).

__Requirements__
* A WebPage [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/WebPage.

__Example__
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/politicalScience/2015/american-revolution-101/index.html",
  "@type": "http://purl.imsglobal.org/caliper/v1/WebPage",
  "name": "American Revolution 101 Landing Page",
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "dateModified": "2015-09-02T11:30:00.000Z",
  "version": "1.0"
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

### Revision History

TODO