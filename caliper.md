#IMS Global Learning Consortium, Inc.

#Caliper Analytics® Specification, version 1.1</h2>

## IPR and Distribution Notices
Recipients of this document are requested to submit, with their comments, notification of any relevant patent claims or other intellectual property rights of which they may be aware that might be infringed by any implementation of the specification set forth in this document, and to provide supporting documentation.

IMS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on IMS’s procedures with respect to rights in IMS specifications can be found at the IMS Intellectual Property Rights web page: [http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Copyright © 2017 IMS Global Learning Consortium. All Rights Reserved.

Use of this specification to develop products or services is governed by the license with IMS found on the IMS website: [http://www.imsglobal.org/license.html](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Permission is granted to all parties to use excerpts from this document as needed in producing requests for proposals.

The limited permissions granted above are perpetual and will not be revoked by IMS or its successors or assigns.

THIS SPECIFICATION IS BEING OFFERED WITHOUT ANY WARRANTY WHATSOEVER, AND IN PARTICULAR, ANY WARRANTY OF NON INFRINGEMENT IS EXPRESSLY DISCLAIMED. ANY USE OF THIS SPECIFICATION SHALL BE MADE ENTIRELY AT THE IMPLEMENTER'S OWN RISK, AND NEITHER THE CONSORTIUM, NOR ANY OF ITS MEMBERS OR SUBMITTERS, SHALL HAVE ANY LIABILITY WHATSOEVER TO ANY IMPLEMENTER OR THIRD PARTY FOR ANY DAMAGES OF ANY NATURE WHATSOEVER, DIRECTLY OR INDIRECTLY, ARISING FROM THE USE OF THIS SPECIFICATION.

## Table of Contents
* 1.0 [Introduction](#introduction)
  * 1.1 [Conventions](#conventions)
  * 1.2 [Terminology](#terminology
* 2.0 [Information Model](#infoModel)
  * 2.1 [Entity](#entity)
  * 2.2 [Event](#event)
  * 2.3 [Metric Profiles](#infoModelProfiles)
      * 2.3.1 [Basic Profile](#basicProfile)
      * 2.3.2 [Annotation Profile](#annotationProfile)
      * 2.3.3 [Assignable Profile](#assignableProfile)
      * 2.3.4 [Assessment Profile](#assessmentProfile)
      * 2.3.5 [Forum Profile](#forumProfile)
      * 2.3.6 [Grading Profile](#gradingProfile)
      * 2.3.7 [Media Profile](#mediaProfile)
      * 2.3.8 [Reading Profile](#readingProfile)
      * 2.3.9 [Session Profile](#sessionProfile)
      * 2.3.10 [Tool Use Profile](#toolUseProfile)
* 3.0 [JSON-LD](#jsonLd)
  * 3.1 [Context](#jsonldContext)
  * 3.2 [Identifiers](#jsonldIdentifiers)
  * 3.3 [Types](#jsonldTypes)
  * 3.2 [Type Coercion](#jsonldTypeCoercion)
  * 3.5 [Processing Algorithms](#jsonldProcessing)
* 4.0 [Sensor API](#sensor)
  * 4.1 [Behavior](#behavior)
  * 4.2 [Envelope](#envelope)
  * 4.3 [Transport](#transport)
  * 4.4 [Endpoint](#endpoint)
  * 4.5 [Endpoint Responses](#endpointResponses)
* 5.0 [Appendix A. Actions](#actions)
* 6.0 [Appendix B. Event Types](#events)
  * 6.1 [AnnotationEvent](#annotationEvent)
  * 6.2 [AssessmentEvent](#assessmentEvent)
  * 6.3 [AssessmentItemEvent](#assessmentItemEvent)
  * 6.4 [AssignableEvent](#assignableEvent)
  * 6.5 [ForumEvent](#forumEvent)
  * 6.6 [MediaEvent](#mediaEvent)
  * 6.7 [MessageEvent](#messageEvent)
  * 6.8 [NavigationEvent](#navigationEvent)
  * 6.9 [OutcomeEvent](#outcomeEvent)
  * 6.10 [ReadingEvent](#readingEvent) (deprecated)
  * 6.11 [SessionEvent](#sessionEvent)
  * 6.12 [ThreadEvent](#threadEvent)
  * 6.13 [ToolUseEvent](#toolUseEvent)
  * 6.14 [ViewEvent](#viewEvent)
* 7.0 [Appendix C. Entity Types](#entities)
  * 7.1 [Agent](#agent)
  * 7.2 [Annotation](#annotation)
  * 7.3 [Assessment](#assessment)
  * 7.4 [AssessmentItem](#assessmentItem)
  * 7.5 [AssignableDigitalResource](#assignableDigitalResource)
  * 7.6 [Attempt](#attempt)
  * 7.7 [AudioObject](#audioObject)
  * 7.8 [BookmarkAnnotation](#bookmarkAnnotation)
  * 7.9 [Chapter](#chapter)
  * 7.10 [CourseOffering](#courseOffering)
  * 7.11 [CourseSection](#courseSection)
  * 7.12 [DigitalResource](#digitalResource)
  * 7.13 [DigitalResourceCollection](#digitalResourceCollection)
  * 7.14 [Document](#document)
  * 7.15 [EpubChapter](#epubChapter) (deprecated)
  * 7.16 [EpubPart](#epubPart) (deprecated)
  * 7.17 [EpubSubChapter](#epubSubChapter) (deprecated)
  * 7.18 [EpubVolume](#epubVolume) (deprecated)
  * 7.19 [FillinBlankResponse](#fillinBlankResponse)
  * 7.20 [Forum](#forum)
  * 7.21 [Frame](#frame)
  * 7.22 [Group](#group)
  * 7.23 [HighlightAnnotation](#highlightAnnotation)
  * 7.24 [ImageObject](#imageObject)
  * 7.25 [LearningObjective](#learningObjective)
  * 7.26 [LtiSession](#ltiSession) 
  * 7.27 [MediaLocation](#mediaLocation)
  * 7.28 [MediaObject](#mediaObject)
  * 7.29 [Membership](#membership)
  * 7.30 [Message](#message)
  * 7.31 [MultipleChoiceResponse](#multipleChoiceResponse)
  * 7.32 [MultipleResponseResponse](#multipleResponseResponse)
  * 7.33 [Organization](#organization)
  * 7.34 [Page](#page)
  * 7.35 [Person](#person)
  * 7.36 [Reading](#reading) (deprecated)
  * 7.37 [Response](#response)
  * 7.38 [Result](#result)
  * 7.39 [Session](#session)
  * 7.40 [SharedAnnotation](#sharedAnnotation)
  * 7.41 [SelectTextResponse](#selectTextResponse)
  * 7.42 [SoftwareApplication](#softwareApplication)
  * 7.43 [TagAnnotation](#tagAnnotation)
  * 7.44 [TrueFalseResponse](#trueFalseResponse)
  * 7.45 [Thread](#thread)
  * 7.46 [VideoObject](#videoObject)
  * 7.47 [WebPage](#webpage)
* 8.0 [Appendix D. Selectors](#selectors)
  * 8.1 [TextPositionSelector](#textPositionSelector)
* 9.0 [Appendix E. Roles](#roles)
* 10.0 [Appendix F. Status](#status)
* 11.0 [Contributors](#contributors)
* 12.0 [References](#references)

<a name="introduction" />
  
## 1.0. Introduction

The drive to deliver education at scale coupled with a demand for measurable accountability | "accountability backed by measurability" has spurred interest in the application of “big data” principles to the business of education.  Opportunities to tap new data sources, ask new questions and pursue new insights have grown as both the learning technology ecosystem has expanded and the definition of what constitutes learning has evolved beyond the formal classroom experience to include informal, social and experiential modes of acquiring knowledge and skills. The challenges inherent in describing, collecting and exchanging learning activity data originating from such diverse learning sources and context are now formidable.

The Caliper Analytics® specification attempts to address the underlying interoperability challenges posed by these shifts in the learning technology landscape.  Caliper provides an information model and domain-specific controlled vocabularies for describing learning activities, events and related entities.  Caliper also defines an application programming interface (the Sensor API™) for marshalling and transmitting Caliper events from instrumented applications to one or more target endpoints for storage, analysis and re-use.  Industry-wide adoption of Caliper offers academic institutions and Ed Tech organizations the tantalizing prospect of a more unified learning data environment in which to build new and innovative services designed to measure, infer, predict, report and visualize.

<a name="conventions" />

### 1.1 Conventions
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](#rfc2119).  A Sensor implementation that fails to implement a MUST/REQUIRED/SHALL requirement or fails to abide by a MUST NOT/SHALL NOT prohibition is considered nonconformant.  SHOULD/SHOULD NOT/RECOMMENDED statements constitute a best practice.  Ignoring a best practice does not violate conformance but a decision to disregard such guidance should be carefully considered.  MAY/OPTIONAL statements indicate that implementors are entirely free to choose whether or not to implement the option.

<a name="definitions" />

### 1.2 Terminology

**TODO review and update these short definitions as necessary.  Add links **

<a name="actorDef" />

__Actor__: An actor specifies an external entity that interacts with a subject, a human user of a designed system or some other system or hardware using services of the subject. An actor is the direct driver of an action. 

<a name="blankNodeDef" />

__Blank Node__: TODO

<a name="actionDef" />

__Action__: something done to accomplish a purpose

<a name="contextDef" />

__Context__: a special [JSON-LD](http://json-ld.org/spec/latest/json-ld/) keyword that maps the terms employed in a JSON document to [IRIs](https://www.ietf.org/rfc/rfc3987.txt) that link to one or more published vocabularies.  Inclusion of a [JSON-LD](http://json-ld.org/spec/latest/json-ld/) context provides an economical way of communicating document semantics to services interested in consuming Caliper event data.

<a name="endpointDef" />

__Endpoint__: a receiver of Caliper messages that is bound to a specific network protocol.  

<a name="entityDef" />

__Entity__: describes an object or a thing that participates in learning-related activity.  Caliper [Entity](#entity) types provide course-grained representations of applications, people, groups and resources that constitute the "stuff" of a Caliper [Event](#event).  Each [Entity](#entity) corresponds to a node in a directed graph.

<a name="eventDef" />

__Event__: describes a relationship established between an actor and an object formed as a result of a purposeful action undertaken by the actor in connection to the object at a particular moment in time.  **TODO what about the context?** 

<a name="jsonldDef" />

__JSON-LD__: a specification providing a JSON-based data serialization and messaging format, processing algorithms and API for working with [Linked Data](#linkedData).  The messages described in this specification are intended to be used in programming environments that support [JSON-LD](http://json-ld.org/spec/latest/json-ld/).

<a name="iriDef" />

__IRI__: The Internationalized Resource Identifier (IRI) extends the Uniform Resource Identifier (URI) scheme by using characters drawn from the Universal Character Set rather than ASCII per [RFC 3987](https://www.ietf.org/rfc/rfc3987.txt).  [Linked Data](#linkedData) rely on IRIs to refer to most nodes and properties.

<a name="iso8601Def" /> 

__ISO 8601__: Caliper data and time values are formatted per ISO 8601 with the addition of millisecond precision.  The format is yyyy-MM-ddTHH:mm:ss.SSSZ where 'T' separates the date from the time while 'Z' indicates that the time is set to UTC.

<a name="linkedDataDef" /> 
 
__Linked Data__: A set of design principles first articulated by Tim Berners-Lee for connecting structured data over the Web.
 
<a name="ltiDef" />
 
__LTI__: Learning Tools Interoperability&reg; (LTI&reg;) is an IMS standard for integration of rich learning applications within educational environments.

<a name="metricProfileDef" />

__Metric Profile__: metric profiles define the information model for caliper.  The caliper metric profiles are organized by activity.

<a name="objectDef" />
 
__Object__: TODO

<a name="sensorDef" />

__Sensor__: Software assets deployed within a learning application to facilitate interaction between the learning application and an event store

<a name="termDef" />

__Term__: a word or short expression that expands to an [IRI](#iriDef) when mapped to a JSON-LD [Context](#contextDef). Terms are employed by Caliper as `type` property string values in order to distinguish between various JSON representations of entities and events defined by the Caliper information model.

<a name="typeCoercionDef" />

__Type Coercion__: TODO

__UUID__: TODO. . . . Each Caliper [Event](#event) is assigned a UUID for the purposes of auditing and retrieval.


<a name="infoModel" />

## 2.0 Information Model 

The Caliper information model defines a set of concepts, rules and relationships for describing learning activities.  Each activity domain modeled is described in a [Metric Profile](#infoModelProfiles).  Each profile is composed of one or more [Event](#event) types.  Each [Event](#event) defines a controlled vocabulary of [actions](#actions) undertaken by learners, instructors and others that are scoped to the event.  Various [Entity](#entity) types representing people, groups and resources are provided in order to better describe both the relationships established between participating entities and the contextual elements relevant to the interaction.

<a name="entity" />

### 2.1 The Caliper Entity
A Caliper [Entity](#entity) is a generic type that represents objects or things that participate in learning-related activities.  [Entity](#entity) is subtyped for enhanced type specificity in order to better describe people, groups, digital content, courses, assignments, assessments, forums, messages, software applications and other entities that constitute the "stuff" of a Caliper [Event](#event).  Each [Entity](#entity) is provisioned with a modest set of attributes that support discovery and description.  As a data structure an [Entity](#entity) constitutes an unordered set of key:value pairs or properties. 

Caliper entities are largely self-describing via a required `type` property.  A unique identifier in the form of an [IRI](#iriDef) MUST also be provided.  [Entity](#entity) [IRI](#iriDef) values MUST be unique as well as valid.  The [IRI](#iriDef) SHOULD be long-lived as well as dereferenceable, i.e., capable of returning a representation of the [Entity](#entity) over HTTP once authorization to access the resource is granted.

**TODO should we state that IRIs/URIs should not employ the URN syntax (implied by dereferenceable which URNs by nature are not)**

Other [Entity](#entity) properties are descriptive in nature or link the [Entity](#entity) to other related entities.  An optional `extensions` property is also defined so that implementors can add custom properties not described by the model.  Certain [Entity](#entity) types like [Annotation](#annotation), [DigitalResource](#digitalResource), [Message](#message) or [Organization](#organization) are provisioned with additional properties in order to allow for a more complete representation of the object.

#### Properties
The base set of [Entity](#entity) properties is listed below.  Each property MUST only be referenced once.  The `id` and `type` properties are required; all other properties are optional.  Custom properties not described by the model MAY be included but MUST be added to the `extensions` property object array as values.  Properties with a value of *null* or empty SHOULD be excluded prior to serialization. 

**TODO If an IRI is deemed inappropriate as an identifier what do we recommend--a blank node?  See 
http://json-ld.org/spec/latest/json-ld/#identifying-blank-nodes**

"It is worth nothing that blank node identifiers may be relabeled during processing. If a developer finds that they refer to the blank node more than once, they should consider naming the node using a dereferenceable IRI so that it can also be referenced from other documents."

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| id | [IRI](#iriDef) | An identifier in the form of a valid [IRI](#iriDef) ~~or a blank node identifier if an [IRI](#iriDef) is deemed inappropriate~~ MUST be specified. The [IRI](#iriDef) MUST be unique and persistent.  The [IRI](#iriDef) SHOULD be dereferenceable; i.e., capable of returning a representation of the [Entity](#entity). | Required |
| type | [Term](#termDef) | A string value corresponding to the [Term](#termDef) defined for the [Entity](#entity) in the external IMS [Caliper context](http://purl.imsglobal.org/ctx/caliper/v1p1) document MUST be specified.  For a generic [Entity](#entity) set the `type` value to the term *Entity*.  If a subtype of [Entity](#entity) is created, set the type to the [Term](#termDef) corresponding to the subtype utilized, e.g., *Person*. | Required |
| name | String | A string value comprising a word or phrase by which the [Entity](#entity) is known MAY be specified. | Optional |
| description | String |  A string value comprising a brief, written representation of the [Entity](#entity) MAY be specified. | Optional |
| dateCreated | DateTime | A date and time value expressed with millisecond precision that describes when the [Entity](#entity) was created MAY be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Optional |
| dateModified | DateTime | A date and time value expressed with millisecond precision that describes when the [Entity](#entity) was last modified MAY be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Optional |
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Entity](#entity). | Optional |

#### Entity Types
[Agent](#agent), [Annotation](#annotation), [Assessment](#assessment), [AssessmentItem](#assessmentItem), [AssignableDigitalResource](#assignableDigitalResource), [Attempt](#attempt), [AudioObject](#audioobject), [BookmarkAnnotation](#bookmarkAnnotation), [Chapter](#chapter), [Collection](#collection), [CourseOffering](#courseOffering), [CourseSection](#courseSection), [DigitalResource](#digitalResource), [Document](#document), [EpubChapter](#epubChapter) (deprecated), [EpubPart](#epubPart) (deprecated), [EpubSubChapter](#epubSubChapter) (deprecated), [EpubVolume](#epubVolume) (deprecated), [FillinBlankResponse](#fillinBlankResponse), [Frame](#frame), [Forum](#forum), [Group](#group), [HighlightAnnotation](#highlightAnnotation), [ImageObject](#imageobject), [LearningObjective](#learningObjective), [LtiSession](#ltiSession), [MediaLocation](#mediaLocation), [MediaObject](#mediaobject), [Membership](#membership), [Message](#message), [MultipleChoiceResponse](#multipleChoiceResponse), [MultipleResponseResponse](#multipleResponseResponse), [Organization](#organization), [Page](#page), [Person](#person), [Reading](#reading) (deprecated), [Response](#response), [Result](#result), [SelectTextResponse](#selectTextResponse), [Session](#session), [SharedAnnotation](#sharedAnnotation), [SoftwareApplication](#softwareapplication), [TagAnnotation](#tagAnnotation), [Thread](#thread), [TrueFalseResponse](#trueFalseResponse), [VideoObject](#videoobject), [WebPage](#webpage)

#### Example
When representing an [Entity](#entity) as [JSON-LD](http://json-ld.org/spec/latest/json-ld/), a `@context` key MUST be embedded in the document with a value that references the external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1).  In cases where an Entity's local context duplicates the active context of an [Event](#event) of which it is a part, the Entity's `@context` property SHOULD be omitted. 

```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "id": "https://example.edu/etexts/201.epub",
    "type": "Document",
    "name": "Example Guide",
    "mediaType": "application/epub+zip",
    "creators": [
        {
            "id": "https://example.edu/people/12345",
            "type": "Person"
        },
        {
            "id": "https://example.com/staff/56789",
            "type": "Person"
        }
    ],
    "dateCreated": "2016-08-01T06:00:00.000Z",
    "datePublished": "2016-10-01T06:00:00.000Z",
    "version": "1.1",
    "extensions": [
        {
            "hostname": "example.docker",
            "request_id": "f72863c5-d541-40b3-8183-e9e3e877e3bc",
            "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36"
        }
    ]
}
```

<a name="event" />

### 2.2 The Caliper Event
A Caliper [Event](#event) is a generic type that describes a relationship established between an `actor` and an `object`, formed as a result of a purposeful [action](#actions) undertaken by the `actor` in connection to the `object` at a particular moment in time. The [Event](#event) properties `actor`, `action` and `object` form a compact data structure that resembles an [RDF](#rdf) triple linking a subject to an object via a predicate.  A learner starting an assessment, annotating a reading, pausing a video or posting a message to a forum are examples of learning activities that Caliper models as events.

Caliper defines a number of [Event](#event) types, each scoped to a particular activity domain.  The event model also seeks to describe the environment or context in which a learning activity is situated.  Group affiliation, membership roles and status, recent navigation history, supporting technology and session information can all be represented.  Entities generated as a result of the interaction between an `actor` and an `object` can also be described (annotating a piece of digital content and producing an [Annotation](#annotation) is one such example).
  
Like an [Entity](#entity), a Caliper [Event](#event) is largely self-describing via a required `type` property.  A unique identifier in the form of a [UUID](https://tools.ietf.org/html/rfc4122) MUST also be provided.  An optional `extensions` property is also defined so that implementors can add custom properties not described by the model.  Again, like an [Entity](#entity), an [Event](#event) as a data structure constitutes an unordered set of key:value pairs or properties.      

#### Properties
The base set of [Event](#event) properties is listed below.  Each property MUST only be referenced once.  The `uuid`, `type`, `actor`, `action`, `object` and `eventTime` properties are required; all other properties are optional.  Custom properties not described by the model MAY be included but MUST be added to the `extensions` property object array as values.  Properties with a value of *null* or empty SHOULD be excluded prior to serialization.

**TODO WHAT VALUE DOES `target` ADD TO AN EVENT THAT CAN'T BE REPRESENTED BY `object`?  DEPRECATE?**

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required |
| type | [Term](#termDef) | A string value corresponding to the [Term](#termDef) defined for the [Event](#event) in the external IMS [Caliper context](http://purl.imsglobal.org/ctx/caliper/v1p1) document MUST be specified.  For a generic [Event](#event) set the `type` to the string value *Event*.  If a subtype of [Entity](#entity) is created, set the `type` to the [Term](#termDef) corresponding to the subtype utilized, e.g., *NavigationEvent*. | Required |
| actor | [Agent](#agent) | The [Agent](#agent) who initiated the [Event](#event), typically a [Person]([#person), [Organization]([#organization) or [SoftwareApplication], MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the actor or subject to the object MUST be specified.  The `action` value range is limited to the set of [actions](#actions) described in this specification and may be further constrained by the chosen [Event](#event) type.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [Entity](#entity) | The [Entity](#entity) that comprises the object of the interaction MUST be specified. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Entity](#entity) | An [Entity](#entity) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional |
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional |
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional |
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional | 
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional |
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example
When representing the [Event](#event) as [JSON-LD](http://json-ld.org/spec/latest/json-ld/), a `@context` key MUST be embedded in the document with a value that references the external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1).

```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "Event",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Created",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/123",
    "type": "Document",
    "name": "Course Syllabus",
    "dateCreated": "2016-11-12T07:15:00.000Z",
    "version": "1"
  },
  "eventTime": "2016-11-15T10:15:00.000Z"
}
```

#### Event Types
[AnnotationEvent](#annotationEvent), [AssignableEvent](#assignableEvent), [AssignmentEvent](#assignmentEvent), [AssignmentItemEvent](#assignmentItemEvent), [ForumEvent](#forumEvent), [MediaEvent](#mediaEvent), [MessageEvent](#messageEvent), [NavigationEvent](#navigationEvent), [OutcomeEvent](#outcomeEvent), [ReadingEvent](#readingEvent) (deprecated), [SessionEvent](#sessionEvent), [ThreadEvent](#threadEvent), [ViewEvent](#viewEvent)

<a name="infoModelProfiles" />

### 2.3 Metric Profiles
**TODO emphasize that Metric Profiles are by their nature opinionated and deliberately so.**

The Caliper information model defines a number of metric profiles, each of which models a learning activity or a supporting activity that helps facilitate learning.  A metric profile's *raison d'etre* is to encourage vocabulary standardization and re-use among application providers delivering complementary, albeit competing capabilities that collect learning activity data.  Each profile provides a domain-specific set of terms and concepts that application designers and developers can draw upon to describe common user interactions in a consistent manner using a shared vocabulary.  Annotating a reading, playing a video, taking a test or grading an assignment submission represent a few examples of the many activities or events that Caliper's metric profiles attempt to describe.
    
Think of each metric profile as a stand-alone, logical container or collection of one or more Caliper events that together help describe a set of inter-related activities.  Each [Event](#event) included in a metric profile describes the expected entities or objects in play as well as provides a controlled vocabulary of required and optional [actions](#actions).  

As an example, the [Forum Profile](#forumProfile) models a set of activities associated with online discussions involving instructors and learners. The profile currently includes a [ForumEvent](#forumEvent), [MessageEvent](#messageEvent), [NavigationEvent](#navigationEvent), [ThreadEvent](#threadEvent) and [ViewEvent](#viewEvent).  An action sequence mediated by the [Forum Profile](#forumProfile) might involve a learner navigating to a forum, subscribing to it, viewing a thread, posting a message in reply to an earlier post and then marking the message as read.
     
Extending Caliper's information model involves designing a new metric profile or enhancing an existing one.  Implementors are free to implement only those Caliper metric profiles as are necessary to model a learning domain.  A video platform provider may decide that only the [Assignable Profile](#assignableProfile), [Media Profile](#mediaProfile) and [Session Profile](#sessionProfile) are relevant to its needs while developers instrumenting an assessment engine would most likely implement the [Assessment Profile](#annotationProfile), [Assignable Profile](#assignableProfile), [Grading Profile](#gradingProfile) and [Session Profile](#sessionProfile).

**Should mention that we encourage implementors to design their own custom profiles**

The following metric profiles are currently available and are summarized individually below:

[Basic Profile](#basicProfile), [Annotation Profile](#annotationProfile), [Assessment Profile](#annotationProfile), [Assignable Profile](#assignableProfile), [Forum Profile](#forumProfile), [Media Profile](#mediaProfile), [Grading Profile](#gradingProfile), [Reading Profile](#readingProfile), [Session Profile](#sessionProfile), [ToolUse Profile](#toolUseProfile)

<a name="basicProfile" />

### 2.3.1 Basic Profile
The Caliper Basic Profile provides a generic [Event](#event) for describing learning or supporting activities that have yet to be modeled by Caliper.

#### Supported events
[Event](#event)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `uuid` |
| ----- | ------  | -------- | -------- | ---------- | ------ |
| [Event](#event) | [Agent](#agent) | [action](#actions) | [Entity](#entity) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |

**TODO Should we restrict the list of supported actions to those not associated with other typed Events?**

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified.  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A generic [Agent](#agent) or one of its subclasses, typically, [Person](#person), [Group](#group), [Organization](#organization) or [SoftwareApplication](#softwareApplication), MUST be specified as the `actor`.
* The `action` value range is limited to the set of [actions](#actions) described in this specification and no other.
* A generic [Entity](#entity) or one of its subclasses MUST be specified as the `object` of the interaction.  
* When navigating to an [Entity](#entity) the [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`.

#### Minimum conformance
Create and send a generic Caliper [Event](#event) to a target [endpoint](#endpoint).  At least one Caliper [action](#actions) MUST be implemented.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "Event",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Created",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/123",
    "type": "Document",
    "name": "Course Syllabus",
    "dateCreated": "2016-11-12T07:15:00.000Z",
    "version": "1"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "uuid": "3a648e68-f00d-4c08-aa59-8738e1884f2c"
}
```

<a name="annotationProfile" />

### 2.3.2 Annotation Profile
The Caliper Annotation Profile models activities related to the annotation of a [DigitalResource](#digitalResource). Creating a bookmark, highlighting selected text, sharing a resource, tagging a document and viewing an annotation are modeled.  The generated [Annotation](#annotation) is also described and is subtyped for greater type specificity.

#### Supported events
[AnnotationEvent](#annotationEvent)

#### Generated annotations
[Annotation](#annotation), [BookmarkAnnotation](#bookmarkAnnotation), [HighlightAnnotation](#highlightAnnotation), [SharedAnnotation](#sharedAnnotation), [TaggedAnnotation](#taggedAnnotation)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `generated` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | ----------- | ------ |
| [AnnotationEvent](#annotationEvent) | [Person](#person) | [Bookmarked](#bookmarked) | [DigitalResource](#digitalResource) | DateTime | [BookmarkAnnotation](#bookmarkAnnotation) |[UUID](https://tools.ietf.org/html/rfc4122) |
| [AnnotationEvent](#annotationEvent) | [Person](#person) | [Highlighted](#highlighted) | [DigitalResource](#digitalResource) | DateTime | [HighlightAnnotation](#highlightAnnotation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AnnotationEvent](#annotationEvent) | [Person](#person) | [Shared](#shared) | [DigitalResource](#digitalResource) | DateTime | [SharedAnnotation](#sharedAnnotation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AnnotationEvent](#annotationEvent) | [Person](#person) | [Tagged](#tagged) | [DigitalResource](#digitalResource) | DateTime | [TagAnnotation](#tagAnnotation) | [UUID](https://tools.ietf.org/html/rfc4122) |

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified when creating an [AnnotationEvent](#annotationEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A [Person](#person) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described below.
* The annotated [DigitalResource](#digitalResource) MUST be specified as the `object` of the interaction.
* Although optional the `generated` [Annotation](#annotation) SHOULD be specified.

#### Minimum conformance
Create and send an [AnnotationEvent](#annotationEvent) to a target [endpoint](#endpoint).  The [Bookmarked](#bookmarked) action is required and MUST be implemented.  All other supported events are considered optional.
 
#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "AnnotationEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "Highlighted",
    "object": {
        "id": "https://example.edu/etexts/201",
        "type": "Document",
        "name": "IMS Caliper Implementation Guide",
        "dateCreated": "2016-10-01T06:00:00.000Z",
        "version": "1.1"
    },
    "generated": {
        "id": "https://example.edu/users/554433/etexts/201/highlights?start=2300&end=2370",
        "type": "HighlightAnnotation",
        "annotator": {
            "id": "https://example.edu/users/554433",
            "type": "Person"
        },
        "annotated": {
            "id": "https://example.edu/etexts/201",
            "type": "Document"
        },
        "selection": {
            "type": "TextPositionSelector",
            "start": 2300,
            "end": 2370
        },
        "selectionText": "ISO 8601 formatted date and time expressed with millisecond precision.",
        "dateCreated": "2016-11-15T10:15:00.000Z"
    },
    "eventTime": "2016-11-15T10:15:00.000Z",
    "uuid": "0067a052-9bb4-4b49-9d1a-87cd43da488a"
}
```

<a name="assessmentProfile" />

### 2.3.3 Assessment Profile
The Caliper Assessment Profile models assessment-related activities including interactions with individual assessment items. Caliper provides [Assessment](#assessment) and [AssessmentItem](#assessmentItem) entities for describing the `object` of these activities as well as a learner's [Attempt](#attempt) for recording a count of the number of times an assigned resource has been attempted.  Five [Response](#response) types are also provided for capturing individual item responses.  Note that the Caliper 1.0 AssessmentItem Profile has been merged into the Assessment Profile.

#### Supported events
[AssessmentEvent](#assessmentEvent), [AssessmentItemEvent](#assessmentItemEvent), [NavigationEvent](#navigationEvent), [ViewEvent](#viewEvent)

#### Generated responses
[Response](#response), [FillinBlankResponse](#fillinBlankResponse), [MultipleChoiceResponse](#multipleChoiceResponse), [MultipleResponseResponse](#multipleResponseResponse), [SelectTextResponse](#selectTextResponse), [TrueFalseResponse](#trueFalseResponse)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `generated` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | ----------- | ------ |
| [AssessmentEvent](#assessmentEvent) | [Person](#person) | [Started](#started) | [Assessment](#assessment) | DateTime | [Attempt](#attempt) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssessmentEvent](#assessmentEvent) | [Person](#person) | [Paused](#paused) | [Assessment](#assessment) | DateTime | [Attempt](#attempt) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssessmentEvent](#assessmentEvent) | [Person](#person) | [Restarted](#restarted) | [Assessment](#assessment) | DateTime | [Attempt](#attempt) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssessmentEvent](#assessmentEvent) | [Person](#person) | [Submitted](#submitted) | [Attempt](#attempt) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) | [Started](#started) | [AssessmentItem](#assessmentItem) | DateTime | [Attempt](#attempt) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) | [Skipped](#skipped)  | [AssessmentItem](#assessmentItem) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) | [Completed](#completed) | [Attempt](#attempt) | DateTime | [Response](#response) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [NavigationEvent](#navigationEvent) | [Person](#person) | [NavigatedTo](#navigatedTo) | [Assessment](#assessment) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ViewEvent](#viewEvent) | [Person](#person) | [Viewed](#viewed) | [Assessment](#assessment) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified when creating an [AssessmentEvent](#assessmentEvent), [AssessmentItemEvent](#assessmentItemEvent), [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A [Person](#person) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* The choice of `object` depends on the action initiated.  For [AssessmentItemEvent](#assessmentItemEvent) [Completed](#completed) and [AssessmentEvent](#assessmentEvent) [Submitted](#submitted) actions the learner's [Attempt](#attempt) MUST be specified as the `object`.  For a [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent) the `object` range is limited to [Assessment](#assessment), [AssessmentItem](#assessmentItem), [Attempt](#attempt), [Response](#response) or one of its subclasses.
* For a [Started](#started) action the [Attempt](#attempt) SHOULD be specified as the `generated` object.  For an [AssessmentItemEvent](#assessmentItemEvent) [Completed](#completed) action, the learner's `generated` [Response](#response) MAY be specified.
* Parent-child relationships that exist between [AssessmentItem](#assessmentItem) and [Assessment](#assessment) attempts MAY be represented via the [Attempt](#attempt) `isPartOf` property.
* When navigating to an [Assessment](#assessment) the [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`.  For an [AssessmentItemEvent](#assessmentItemEvent) the prior [AssessmentItem](#assessmentItem), if known, MAY be specified as the `referrer`.

#### Minimum conformance
Create and send an [AssessmentEvent](#assessmentEvent) to a target [endpoint](#endpoint).  The [Started](#started) and [Submitted](#submitted) actions are required and MUST be implemented.  All other supported events are considered optional. 

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "AssessmentEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "Started",
    "object": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment"
    },
    "generated": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
        "type": "Attempt",
        "assignee": {
            "id": "https://example.edu/users/554433",
            "type": "Person"
        },
        "assignable": {
            "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
            "type": "Assessment"
        },
        "count": 1,
        "dateCreated": "2016-11-15T10:15:00.000Z",
        "startedAtTime": "2016-11-15T10:15:00.000Z"
    },
    "eventTime": "2016-11-15T10:15:00.000Z",
    "uuid": "27734504-068d-4596-861c-2315be33a2a2"
}
```

<a name="assignableProfile" />

### 2.3.4 Assignable Profile
The Assignable Profile models activities associated with digital content assigned to a learner for completion according to specific criteria.  Caliper provides a generic [AssignableDigitalResource](#assignableDigitalResource) for describing the `object` of these activities as well as a learner's [Attempt](#attempt) for recording a count of the number of times an assigned resource has been attempted. 

#### Supported events
[AssignableEvent](#assignableEvent), [NavigationEvent](#navigationEvent), [ViewEvent](#viewEvent)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `generated` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | ----------- | ------ |
| [AssignableEvent](#assignableEvent) | [Person](#person) | [Started](#started) | [AssignableDigitalResource](#assignableDigitalResource) | DateTime | [Attempt](#attempt) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssignableEvent](#assignableEvent) | [Person](#person) | [Completed](#completed) | [Attempt](#attempt) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssignableEvent](#assignableEvent) | [Person](#person) | [Activated](#activated) | [AssignableDigitalResource](#assignableDigitalResource) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssignableEvent](#assignableEvent) | [Person](#person) | [Deactivated](#deactivated) | [AssignableDigitalResource](#assignableDigitalResource) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [AssignableEvent](#assignableEvent) | [Person](#person) | [Reviewed](#reviewed) | [Attempt](#attempt) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [NavigationEvent](#navigationEvent) | [Person](#person) | [NavigatedTo](#navigatedTo) | [AssignableDigitalResource](#assignableDigitalResource) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ViewEvent](#viewEvent) | [Person](#person) | [Viewed](#viewed) | [AssignableDigitalResource](#assignableDigitalResource) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |

**TODO: Do we need to add a submitted action or replace "completed" with "submitted" so that we align this set of actions with the AssessmentEvent submitted actions?**

#### Requirements 
* Certain [Event](#event) properties are required and MUST be specified when creating an [AssignableEvent](#assignableEvent), [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A [Person](#person) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* For [AssignableEvent](#assignableEvent) [Completed](#completed), [Submitted](#submitted) or [Reviewed](#reviewed) actions the learner's [Attempt](#attempt) MUST be specified as the `object` of the interaction; otherwise the [Attempt](#attempt) SHOULD be specified as the `generated` object.  For a [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent) the `object` of the interaction is limited to [AssignableDigitalResource](#assignableDigitalResource), one of it subclasses, or a learner's [Attempt](#attempt).
* When navigating to an [AssignableDigitalResource](#assignableDigitalResource) the [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`.

#### Minimum conformance
Create and send an [AssignableEvent](#assignableEvent) to a target [endpoint](#endpoint). The [Started](#started) and [Completed](#completed) actions are required and MUST be implemented.  All other supported events are considered optional. 

#### Example

```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "AssignableEvent",
    "actor": {
        "id": "https://example.edu/users/112233",
        "type": "Person"
    },
    "action": "Activated",
    "object": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment",
        "name": "Quiz One",
        "datePublished": "2016-11-12T10:10:00.000Z",
        "dateToStartOn": "2016-11-14T05:00:00.000Z",
        "dateToSubmit": "2016-11-18T11:59:59.000Z",
        "maxAttempts": 2,
        "maxSubmits": 2,
        "maxScore": 25
    },
    "eventTime": "2016-11-12T10:15:00.000Z",
    "uuid": "2635b9dd-0061-4059-ac61-2718ab366f75"
}
```

<a name="forumProfile" />

### 2.3.5 Forum Profile
The Caliper Forum Profile models learners and others participating in online forum communities.  Forums typically encompass one or more threads or topics to which members can subscribe, post messages and reply to other messages if a threaded discussion is permitted.  Caliper provides [Forum](#forum), [Thread](#thread) and [Message](#message) entities for representing the `object` of these activities.

#### Supported events
[ForumEvent](#forumEvent), [MessageEvent](#messageEvent), [NavigationEvent](#navigationEvent), [ThreadEvent](#threadEvent), [ViewEvent](#viewEvent)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `uuid` |
| ----- | ------  | -------- | -------- | ---------- | ------ |
| [ForumEvent](#forumEvent) | [Person](#person) | [Subscribed](#subscribed) | [Forum](#forum) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ForumEvent](#forumEvent) | [Person](#person) | [Unsubscribed](#unsubscribed) | [Forum](#forum) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MessageEvent](#messageEvent) | [Person](#person) | [MarkedAsRead](#markedAsRead) | [Message](#message) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MessageEvent](#messageEvent) | [Person](#person) | [markedAsUnRead](#markedAsUnRead) | [Message](#message) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MessageEvent](#messageEvent) | [Person](#person) | [Posted](#posted) | [Message](#message) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [NavigationEvent](#navigationEvent) | [Person](#person) | [NavigatedTo](#navigatedTo) | [Forum](#forum), [Message](#message), [Thread](#thread) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ThreadEvent](#threadEvent) | [Person](#person) | [MarkedAsRead](#markedAsRead) | [Thread](#thread) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ThreadEvent](#threadEvent) | [Person](#person) | [markedAsUnRead](#markedAsUnRead) | [Thread](#thread) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ViewEvent](#viewEvent) | [Person](#person) | [Viewed](#viewed) | [Forum](#forum), [Message](#message), [Thread](#thread) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |

#### Requirements 
* Certain [Event](#event) properties are required and MUST be specified when creating a [ForumEvent](#forumEvent), [MessageEvent](#messageEvent), [NavigationEvent](#navigationEvent), [ThreadEvent](#threadEvent) or [ViewEvent](#viewEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A [Person](#person) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* For a [ForumEvent](#forumEvent) the `object` range is limited to [Forum](#forum); for a [ThreadEvent](#threadEvent) the `object` range is limited to [Thread](#thread); for a [MessageEvent](#messageEvent) the `object` range is limited to [Message](#message); for a [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent) the `object` range is limited to [Forum](#forum), [Thread](#thread) or [Message](#message).
* When a [MessageEvent](#messageEvent) represents a reply, the prior [Message](#message) that prompted the reply SHOULD be referenced via the [Message](#message) `replyTo` property.
* Parent-child relationships that exist between a [Message](#message), [Thread](#thread) and a [Forum](#forum) MAY be represented by judicious use of the inherited [DigitalResource](#digitalResource) `isPartOf` property.
* When navigating to a [Forum](#forum), [Thread](#thread) or [Message](#message) the [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`.

#### Minimum conformance
Create and send a [MessageEvent](#messageEvent) to a target endpoint. The [Posted](#posted) action is required and MUST be implemented.  All other supported events are considered optional.

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "MessageEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "Posted",
    "object": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/2",
        "type": "Message",
        "name": "Caliper MessageEvent example",
        "body": "Posting a Message referencing its parent Thread and Forum.",
        "isPartOf": {
            "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1",
            "type": "Thread",
            "isPartOf": {
                "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2",
                "type": "Forum"
            }
        },
        "dateCreated": "2016-11-15T10:15:00.000Z"
    },
    "eventTime": "2016-11-15T10:15:00.000Z",
    "uuid": "0d015a85-abf5-49ee-abb1-46dbd57fe64e"
}
```

<a name="gradingProfile" />

### 2.3.6 Grading Profile
The Caliper Grading Profile models grading activities performed by an [Agent](#agent), typically a [Person](#person) or a [SoftwareApplication](#softwareApplication).  Grading a learner's [Attempt](#attempt) of an [AssignableDigitalResource](#assignableDigitalResource) and generating a [Result](#result) is modeled. The Grading Profile replaces the Caliper 1.0 Outcomes Profile.

#### Supported events
[OutcomeEvent](#outcomeEvent)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `generated` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | ----------- | ------ |
| [OutcomeEvent](#outcomeEvent) | [Agent](#agent) | [Graded](#graded) | [Attempt](#attempt) | DateTime | [Result](#result) | [UUID](https://tools.ietf.org/html/rfc4122) |

**TODO: ADD ViewEvent, as in view the Result?**

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified when creating an [OutcomeEvent](#outcomeEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A generic [Agent](#agent) or one of its subclasses, typically, [Person](#person), [Group](#group), [Organization](#organization) or [SoftwareApplication](#softwareApplication), MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* The learner's [Attempt](#attempt) MUST be specified as the `object` of the interaction.
* The `generated` [Result](#result) SHOULD also be specified.

#### Minimum conformance
Create and send a Caliper [OutcomeEvent](#outcomeEvent) to a target endpoint.  The [Graded](#graded) action is required and MUST be implemented.

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "OutcomeEvent",
    "actor": {
        "id": "https://example.edu/autograder",
        "type": "SoftwareApplication"
    },
    "action": "Graded",
    "object": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
        "type": "Attempt",
        "assignee": {
            "id": "https://example.edu/users/554433",
            "type": "Person"
        },
        "assignable": {
            "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
            "type": "Assessment"
        },
        "count": 1,
        "dateCreated": "2016-11-15T10:05:00.000Z",
        "startedAtTime": "2016-11-15T10:05:00.000Z",
        "endedAtTime": "2016-11-15T10:55:12.000Z",
        "duration": "PT50M12S"
    },
    "eventTime": "2016-11-15T10:57:06.000Z",
    "generated": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/results/1",
        "type": "Result",
        "attempt": {
            "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
            "type": "Attempt"
        },
        "normalScore": 15,
        "totalScore": 15,
        "scoredBy": {
            "id": "https://example.edu/autograder",
            "type": "SoftwareApplication"
        },
        "dateCreated": "2016-11-15T10:55:05.000Z"
    },
    "uuid": "a50ca17f-5971-47bb-8fca-4e6e6879001d"
}
```

<a name="mediaProfile" />

### 2.3.7 Media Profile
The Caliper Media Profile models interactions between learners and rich content such as audio, images and video.  Implementors can leverage a number of media-related entities including [AudioObject](#audioObject), [ImageObject](#audioObject) and [VideoObject](#videoObject), each subtyped from a generic [MediaObject](#mediaObject).  A [MediaLocation](#mediaLocation) entity is also provided in order to represent the current location in an audio or video stream.

#### Supported events
[MediaEvent](#mediaEvent), [NavigationEvent](#navigationEvent), [ViewEvent](#viewEvent) 
 
#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `target` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | -------- | ------ |
| [MediaEvent](#mediaEvent) | [Person](#person) | [Started](#started) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [Paused](#paused) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [Resumed](#resumed) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [Ended](#ended) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [ForwardedTo](#forwardedTo) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [JumpedTo](#jumpedTo) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [Rewound](#rewound) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [ChangedResolution](#changedResolution) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [ChangedSize](#changedSize) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [ChangedSpeed](#changedSpeed) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [ChangedVolume](#changedVolume) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [EnabledClosedCaptioning](#enabledClosedCaptioning) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [DisabledClosedCaptioning](#disabledClosedCaptioning) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [EnteredFullScreen](#enteredFullScreen) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [ExitedFullScreen](#exitedFullScreen) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [Muted](#muted) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [Unmuted](#unmuted) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [OpenedPopout](#openedPopout) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [MediaEvent](#mediaEvent) | [Person](#person) | [ClosedPopout](#closedPopout) | [MediaObject](#mediaObject) | DateTime | [MediaLocation](#mediaLocation) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [NavigationEvent](#navigationEvent) | [Person](#person) | [NavigatedTo](#navigatedTo) | [MediaObject](#mediaObject) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ViewEvent](#viewEvent) | [Person](#person) | [Viewed](#viewed)  | [MediaObject](#mediaObject) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified when creating a [MediaEvent](#mediaEvent), [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A [Person](#person) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* A [MediaObject](#mediaObject) or one of its subclasses MUST be specified as the `object` of the interaction.
* A [MediaLocation](#mediaLocation) MAY be specified as the `target` in order to indicate the current location in an audio or video stream.
* When navigating to a [MediaObject](#mediaObject) or one of its subclasses the [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`.
* For a [MediaEvent](#mediaEvent) the `object` range is limited to [MediaObject](#mediaObject) or its subclasses; for a [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent) the `object` of the interaction is limited to [MediaObject](#mediaObject) or one of it subclasses.

#### Minimum conformance
Create and send a [MediaEvent](#mediaEvent) to a target endpoint. The [Started](#started), [Paused](#paused), [Resumed](#resumed) and [Ended](#ended) actions are required and MUST be implemented.  All other supported events are considered optional.

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "MediaEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "Paused",
    "object": {
        "id": "https://example.edu/UQVK-dsU7-Y",
        "type": "VideoObject",
        "mediaType": "video/ogg",
        "duration": "PT20M20S"
    },
    "target": {
        "id": "https://example.edu/UQVK-dsU7-Y?t=321",
        "type": "MediaLocation",
        "currentTime": "PT05M21S"
    },
    "eventTime": "2016-11-15T10:15:00.000Z",
    "uuid": "956b4a02-8de0-4991-b8c5-b6eebb6b4cab"
}
```

<a name="readingProfile" />

### 2.3.8 Reading Profile
The Caliper Reading Profile models activities associated with navigating to and viewing textual content. Implementors can leverage a number of entities representing digital content such as [Document](#document), [Chapter](#chapter), [Page](#page), [WebPage](#webPage) and [Frame](#frame), each subtyped from [DigitalResource](#digitalResource).

#### Supported events
[NavigationEvent](#navigationEvent), [ViewEvent](#viewEvent) 

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `target` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | -------- | ------ |
| [NavigationEvent](#navigationEvent) | [Person](#person) | [NavigatedTo](#navigatedTo) | [DigitalResource](#digitalResource) | DateTime | [Frame](#frame) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [ViewEvent](#viewEvent) | [Person](#person) | [Viewed](#viewed) | [DigitalResource](#digitalResource) | DateTime | [Frame](#frame) | [UUID](https://tools.ietf.org/html/rfc4122) |

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified when creating a [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A [Person](#person) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* For a [NavigationEvent](#navigationEvent) or [ViewEvent](#viewEvent) the `object` of the interaction is limited to [DigitalResource](#digitalResource) or one of it subclasses.
* If relevant, a [Frame](#frame) MAY be specified as the `target` in order to indicate an indexed segment or location.
* When navigating to a [DigitalResource](#digitalResource) or one of its subclasses the [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`.

#### Minimum conformance
Create and send a [NavigationEvent](#navigationEvent) and a [ViewEvent](#viewEvent) to a target endpoint.  The [NavigatedTo](#navigatedTo) and [Viewed](#viewed) actions are required and MUST be implemented.

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "NavigationEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "NavigatedTo",
    "object": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/pages/2",
        "type": "WebPage"
    },
    "eventTime": "2016-11-15T10:15:00.000Z",
    "referrer": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/pages/1",
        "type": "WebPage"
    },
    "uuid": "ff9ec22a-fc59-4ae1-ae8d-2c9463ee2f8f"
}
```

<a name="sessionProfile" />

### 2.3.9 Session Profile
The Caliper Session Profile models the creation and subsequent termination of a user session established by a [Person](#person) interacting with a [SoftwareApplication](#softwareApplication).  A [Session](#session) entity is described for representing the user session.

#### Supported events
[SessionEvent](#sessionEvent)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `session` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | --------- | ------ |
| [SessionEvent](#sessionEvent) | [Person](#person) | [LoggedIn](#loggedIn) | [SoftwareApplication](#softwareApplication) | DateTime | [Session](#session) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [SessionEvent](#sessionEvent) | [Person](#person) | [LoggedOut](#loggedOut) | [SoftwareApplication](#softwareApplication) | DateTime | [Session](#session) | [UUID](https://tools.ietf.org/html/rfc4122) |
| [SessionEvent](#sessionEvent) | [SoftwareApplication](#softwareApplication) | [TimedOut](#timedOut) | [Session](#session) | DateTime | &nbsp; | [UUID](https://tools.ietf.org/html/rfc4122) |

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified when creating a [SessionEvent](#sessionEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* The choice of `actor` depends on the action initiated.  For [LoggedIn](#loggedIn) and [LoggedOut](#loggedOut) actions a [Person](#person) MUST be specified as the `actor`.  For a [TimedOut](#timedOut) action a [SoftwareApplication](#softwareApplication) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* When logging in to a [SoftwareApplication](#softwareApplication), if the actor is attempting to access a particular [DigitalResource](#digitalResource) it MAY be designated as the `target` of the interaction.
* When logging in or out of a [SoftwareApplication](#softwareApplication), the [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`.
* Although the [SessionEvent](#sessionEvent) `session` property is optional, the relevant user [Session](#session) SHOULD be specified.

#### Minimum conformance
Create and send a [SessionEvent](#sessionEvent) to a target endpoint. The [LoggedIn](#loggedIn) action is required and MUST be implemented.

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "SessionEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "LoggedIn",
    "object": {
        "id": "https://example.edu",
        "type": "SoftwareApplication"
    },
    "eventTime": "2016-11-15T10:15:00.000Z",
    "session": {
        "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
        "type": "Session"
    },
    "uuid": "fcd495d0-3740-4298-9bec-1154571dc211"
}
```

<a name="toolUseProfile" />

### 2.3.10 Tool Use Profile
The Caliper Tool Use Profile models an intended interaction between a user and a tool.  In other words, when a [Person](#person) utilizes a [SoftwareApplication](#softwareApplication) in a manner that the application determines to be its "intended use for learning", an application that implements the Tool Use Profile can emit a [ToolUseEvent](#toolUseEvent) indicating such usage.

#### Supported events
[ToolUseEvent](#toolUseEvent)

#### Supported actions
| Event | `actor` | `action` | `object` | `dateTime` | `uuid` |
| ----- | ------- | -------- | -------- | ---------- | ------ |
| [ToolUseEvent](#toolUseEvent) | [Person](#person) | [Used](#used) | [SoftwareApplication](#softwareApplication) | DateTime | [UUID](https://tools.ietf.org/html/rfc4122) |

#### Requirements
* Certain [Event](#event) properties are required and MUST be specified when creating a [ToolUseEvent](#toolUseEvent).  Required properties include `type`, `actor`, `action`, `object`, `eventTime` and `uuid`.  All other [Event](#event) properties are considered optional.
* A [Person](#person) MUST be specified as the `actor`.
* The `action` value range is scoped by event and limited to the supported actions described above.
* A [SoftwareApplication](#softwareApplication) MUST be specified as the `object` of the interaction.

#### Minimum conformance
Create and send a Caliper [ToolUseEvent](#toolUseEvent) to a target endpoint.  The [Used](#used) action is required and MUST be implemented.

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "type": "ToolUseEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "Used",
    "object": {
        "id": "https://example.edu",
        "type": "SoftwareApplication"
    },
    "eventTime": "2016-11-15T10:15:00.000Z",
    "uuid": "7e10e4f3-a0d8-4430-95bd-783ffae4d916"
}
```

<a name="jsonLd" />

## 3.0 JSON-LD
Over the last decade the advent of cloud-based, networked applications have led to changes in the way data is structured and represented.  Data once considered strictly hierarchical like a curriculum, a course roster or a transcript now frequently link out to other kinds of data.  Modeling bundles of data pointing to other bundles of data now requires thinking in terms of graphs and [Linked Data](#linkedData).  Caliper [Event](#event) data presents us with similar structures.  A Caliper [Event](#event) links to user data, digital content, courses and rosters, grades and credentials, institutional and organizational data, application and session data and so on.  [JSON-LD](#jsonldDef), Caliper's chosen syntax for describing learning activity data as [Linked Data](#linkedData) using a JSON-based interchange format, provides the necessary representational horsepower to describe these kinds of data linkages and specify how data is to be understood when published and shared across a network.  

The [Linked Data](#linkedData) principles first outlined by Tim Berners-Lee that inform today’s Semantic Web technologies also influence [JSON-LD](#jsonldDef) and Caliper: use [IRIs](#iriDef)/URIs as names for things; use HTTP [IRIs](#iriDef)/URIs so that information about things (e.g., people, objects, concepts) can be retrieved ~~using a standard format~~; link out to other relevant things by way of their [IRIs](#iriDef)/URIs in order to ~~encourage~~ promote discovery of new relationships between things.  [JSON-LD](#jsonldDef) abides by these “rules”. It features a lightweight syntax and a JSON-based format for serializing [Linked Data](#linkedData).  [JSON-LD](#jsonldDef) encourages use of globally unique, persistent, dereferenceable [IRIs](#iriDef) for entities (i.e., nodes) and attributes.  [JSON-LD](#jsonldDef) also provides a means of expressing relationships between entities as a directed graph.  Crucially, for machine-to-machine data exchange, [JSON-LD](#jsonldDef) provides Caliper with a mechanism for rendering comprehensible the underlying semantics of its JSON-based documents via a mapping of its [Terms](#terms) to one or more published vocabularies.  In a world where learners now interact with an array of learning applications the need to aggregate data streams generated from multiple sources in order to discern patterns and behaviors that transcend application boundaries is of vital importance. 

<a name="jsonldContext" />

### 3.1 Context
**TODO FORBID OVERRIDING OF CALIPER DEFINED KEYS, i.e., caliper:Person overridden as schema:Person by a trailing local context.**

Caliper [JSON-LD](#jsonldDef) documents feature a context, denoted by the `@context` keyword, that is employed to map document [Terms](#termDef) to [IRIs](#iriDef) that then link out to one or more controlled vocabularies.  Inclusion of a [JSON-LD](#jsonldDef) context provides an economical way for Caliper to communicate document semantics to services interested in consuming Caliper event data.

[JSON-LD](#jsonldDef) contexts can be inserted inline or located in a file external to the document and referenced.  In the case of Caliper an external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1) is available and MUST be referenced in Caliper [JSON-LD](#jsonldDef) documents.  Each Caliper [Event](#event) and [Entity](#entity) describe emitted by a [Sensor](#sensor) MUST be provisioned with a `@context` key that provides a context definition.  That said, defining a context for an [Entity](#entity) that duplicates a local [Event](#event) context SHOULD be avoided.  In cases where a duplicate context exists in a Caliper JSON-LD document it SHOULD be omitted when serializing the object.  

**TODO craft a new example, this is one is used elsewhere**

#### Example: remote Caliper context
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "Event",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Created",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/123",
    "type": "Document",
    "name": "Course Syllabus",
    "dateCreated": "2016-11-12T07:15:00.000Z",
    "version": "1"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "uuid": "3a648e68-f00d-4c08-aa59-8738e1884f2c"
}
```

<a name="jsonldIdentifiers" />

### 3.2 Identifiers
[Linked Data](#linkedData) relies on [IRIs](#iriDef)/URIs for the identification and retrieval of resources.  Likewise, [JSON-LD](#jsonldDef) specifies the use of [IRIs](#iriDef) for identifying most nodes (i.e., JSON objects) and their attributes.  In JSON-LD, IRIs may be represented either as an absolute IRI containing a scheme, path and optional query and fragment segments or as a relative IRI minus the scheme and/or domain that is resolved relative to a base IRI.  If an [IRI](#iriDef) is deemed inappropriate for the resource a [blank node](#blankNodeDef) identifier may be assigned.  [JSON-LD](#jsonldDef) provides a special `@id` keyword for assigning identifiers to nodes.
   
In Caliper, the [JSON-LD](#jsonldDef) `@id` keyword is aliased as `id` in the external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1).  This is done in order to avoid the temptation of employing [JSON-LD](#jsonldDef) keywords as JSON object property names and is aligned with [JSON-LD](#jsonldDef) community practice.  Thus, each Caliper [Entity](#entity) described by the information model is provisioned with an `id` rather than `@id` property for identifying the resource.  

Every [Entity](#entity) associated with a Caliper [Event](#event) MUST be assigned an `id` in the form of a valid [IRI](#iriDef) or a blank node identifier. The [IRI](#iriDef) MUST be unique and persistent.  The [IRI](#iriDef) SHOULD be dereferenceable; i.e., capable of returning a representation of the [Entity](#entity).  Use of the URN scheme in place of an [IRI](#iriDef) is inappropriate since such an identifier precludes the possibility of locating and retrieving the named resource.

A Caliper [JSON-LD](#jsonldDef) document is a representation of a directed graph.  Each [Entity](#entity) described therein is a node in the graph.  The enclosing [Event](#event) is not considered a graph element and is instead identified by a [UUID](#uuidDef) for the purposes of auditing and retrieval.

**TODO Is the above UUID rationale sufficient? Satisfy ourselves that the enclosing Event is not a graph element--i.e., not a node type?  Requirements: 1) exists outside of a JSON-LD context, 2) does not contain the @value, @list, or @set keywords, 3) is NOT the top-most JSON object in the JSON-LD document consisting of no other members than @graph and @context. See http://json-ld.org/spec/latest/json-ld/#node-objects**

<a name="jsonldTypes" />

### 3.3 Types
[JSON-LD](#jsonldDef) employs the `@type` keyword to indicate the data type of a node or typed value.  As with the aliasing of the `@id` keyword, `@type` is aliased as `type` in the external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1) in keeping with [JSON-LD](#jsonldDef) community practice.  [JSON-LD](#jsonldDef) employs a number of different mechanisms for expressing typed values.  The IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1) currently includes the following typed values: node types, value types and object properties with values that are mapped to a [Term](#term) defined in the active context. 

As the example below illustrates, the node type specifies the type of [Entity](#entity) being described like a [Person](#person) or [Message](#message) in the example below.  A value type specifies the data type of particular value like a string, integer, boolean or date.  [Terms](#term) such as `body`, `dateCreated`, `eventTime` and `uuid` are typed in this way.  An object property like `action` in the example references a `@vocab` keyword indicating that the property value is mapped to a [Term](#term) defined in the active context, in this case `Posted`. 

#### Example: embedded context featuring keyword aliasing, node types, value types and an object property with a @vocab mapping
```json
{
    "@context": {
        "id": "@id",
        "type": "@type",
        "caliper": "http://purl.imsglobal.org/caliper/",
        "verb": "http://purl.imsglobal.org/vocab/caliper/action#",
        "xsd": "http://www.w3.org/2001/XMLSchema#",
        "MessageEvent": "caliper:MessageEvent",
        "Message": "caliper:Message",
        "actor": "caliper:actor",
        "action": {"@id": "caliper:action", "@type": "@vocab"},
        "object": "caliper:object",
        "body": {"@id": "caliper:body", "@type": "xsd:string"},
        "dateCreated": {"@id": "caliper:dateCreated", "@type": "xsd:dateTime"},
        "eventTime": {"@id": "caliper:eventTime", "@type": "xsd:dateTime"},
        "uuid": {"@id": "caliper:uuid", "@type": "xsd:string"},
        "Posted": "verb:Posted"
    },
    "type": "MessageEvent",
    "actor": {
        "id": "https://example.edu/users/554433",
        "type": "Person"
    },
    "action": "Posted",
    "object": {
        "id": "https://example.edu/sections/1/forums/2/topics/1/messages/2",
        "type": "Message",
        "body": "What does Caliper Event JSON-LD look like?",
        "dateCreated": "2017-12-15T10:15:00.000Z"
    },
    "eventTime": "2017-12-15T10:15:00.000Z",
    "uuid": "0d015a85-abf5-49ee-abb1-46dbd57fe64e"
}
```
<a name="jsonldTypeCoercion" />

### 3.4 Type Coercion
[JSON-LD](http://json-ld.org/spec/latest/json-ld/) supports the *coercion* of values to particular data types.  Certain Caliper JSON object property values described in the external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1) MAY be coerced to a string identifier by "layering" an embedded context over the Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1).  Duplicate context terms are overridden by [JSON-LD](http://json-ld.org/spec/latest/json-ld/) using a most-recently-defined-wins mechanism.    

Coercing object properties requires an explicit declaration in the active context.  The following example demonstrates the use of an inline context object to coerce both the `actor` and `object` property values to their respective `@id` values (aliased as `id').

```json
{
    "sensor": "https://example.edu/sensors/1",
    "sendTime": "2016-11-15T11:05:01.000Z",
    "dataVersion": "http://purl.imsglobal.org/ctx/caliper/v1p1",
    "data": [
        {
            "@context": [
                "http://purl.imsglobal.org/ctx/caliper/v1p1",
                {
                    "actor": { "id": "Person", "type": "id" },
                    "object": { "id": "Document", "type": "id" }
                }
            ],
            "type": "Event",
            "actor": "https://example.edu/users/554433",
            "action": "Created",
            "object": "https://example.edu/terms/201701/courses/7/sections/1/resources/27",
            "eventTime": "2016-11-15T10:15:00.000Z",
            "uuid": "7025d2f8-c76c-44b8-9d98-593d7969177f"
        }
    ]
}
```
A Caliper [Sensor](#sensor) MAY send an [Event](#event) or [Entity](#entity) that includes an array of local contexts to indicate that one or more object property values are to be coerced to an [IRI](#iriDef).  The external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1) value MUST be listed first in the `@context` array.  Additional inline contexts MUST then be added that identify which object properties are to be coerced.  The following format applies where the `edApp` [Term](#term) serves as an example object property with an (aliased) `id` used as value to indicate the string value of [Term](#coerced) is to be interpreted as an [IRI](#iriDef) within the body of the JSON-LD document. 
  
```json
{
  "edApp": {"id": "SoftwareApplication", "type": "id"}
}

```  

An [Endpoint](#endpoint) must be capable of interpreting coerced values of this type as [Entity](#entity) identifiers.  The receiver of a Caliper [Event](#event) or [Entity](#entity) with coerced object properties but lacking an explicit declaration embedded in an inline context will be considered nonconformant.

<a name="jsonldProcessing" />

### 3.5 Processing Algorithms
**TODO Provide the briefest of overviews (OR NOT).  Make clear that endpoints are not required to utilize JSON-LD parsers to transform Caliper JSON-LD documents.**

[JSON-LD](#jsonldDef) defines a number of processing algorithms for transforming JSON-LD documents. . . .  

* expansion
* compaction
* flattening
* RDF serialization/deserialization.

<a name="sensor" />

## 4.0 Sensor API™
Caliper defines an application programming interface (the Sensor API™) for marshalling and transmitting data to a target endpoints.  Adopting one or more [metric profiles](#metricProfiles) ensures adherence to the information model; implementing the [Sensor](#sensor) provides instrumented platforms, applications and services with a transport interface for communicating with data consumers.

<a name="sensorBehavior" />

### 4.1 Behavior
A Caliper [Sensor](#sensor) MUST be capable of performing the following operations:

* send events: i.e., emit a Caliper [Envelope](#envelope) containing a `data` payload consisting of one or more Caliper [Event](#event) types to a target endpoint.
* describe entities: i.e., emit a Caliper [Envelope](#envelope) containing a `data` payload consisting of one or Caliper [Entity](#entity) types to a target endpoint.

A [Sensor](#sensor) MAY be assigned other responsibilities such as creating and validating Caliper entities and events but such capabilities need not be exposed to external data consumers.  

<a name="envelope" />

### 4.2 Envelope
**TODO Confirm that we will permit the Sensor to send mixed payloads of Entity describes/Events.  I'm +1.**

Caliper [Event](#event) and [Entity](#entity) data are transmitted inside an [Envelope](#envelope), a purpose-built JSON data structure that includes metadata about the emitting [Sensor](#sensor) and the data payload.  Each [Event](#event) and [Entity](#entity) "describe" included in an envelope's `data` payload messages MUST be expressed as a [JSON-LD](http://json-ld.org/spec/latest/json-ld/) document. 

#### Properties
Caliper [Envelope](#envelope) properties are listed below.  The `sensor`, `sendTime`, `dataVersion` and `data` properties are required.  Each property MUST only be referenced once.  No custom properties are permitted.

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| sensor | String | A unique identifier assigned either to the [Sensor](#sensor) or to the instrumented platform, application or service utilizing the [Sensor](#sensor) MUST be specified.  The identifier SHOULD be in the form of an [IRI](#iriDef). | Required |
| sendTime | DateTime | A date and time string value expressed with millisecond precision that indicates the time at which the [Sensor](#sensor) issued the message MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| dataVersion | String | A string value indicating which version of the IMS Caliper Analytics® specification governs the form of the Caliper entities and events contained in the `data` payload MUST be specified. The value MUST be set to the IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1) [IRI](#iriDef) used to resolve the meanings of the `data` payload's terms and values. | Required |
| data | Array | An ordered collection of one or more Caliper [Entity](#entity) describes and/or [Event](#event) types.  The Sensor MAY mix describes and events in the same [Envelope](#envelope). | Required |

#### Example
```json
{
   "sensor": "https://example.edu/sensors/1",
   "sendTime": "2016-11-15T11:05:01.000Z",
   "dataVersion":  "http://purl.imsglobal.org/ctx/caliper/v1p1/Context",
   "data": [
    {
      "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1/Context",
      "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/1/syllabus.pdf",
      "type": "DigitalResource",
      "name": "Course Syllabus",
      "mediaType": "application/pdf",
      "creators": [
        {
          "id": "https://example.edu/users/223344",
          "type": "Person"
        }
      ],
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/1",
        "type": "DigitalResourceCollection",
        "name": "Course Assets",
        "isPartOf": {
          "id": "https://example.edu/terms/201601/courses/7/sections/1",
          "type": "CourseSection"
        }
      },
      "dateCreated": "2016-08-02T11:32:00.000Z"
    }
   ]
}
```

### 4.x Sending Events


### 4.x Sending Describes


<a name="transport" />

### 4.3 Transport

**Should we define custom headers for Caliper version, payload type?**

A [Sensor](#sensor) MUST be capable of communicating with a Caliper [Endpoint](#endpoint) using the HTTP POST request method; note that the IMS Caliper certification suite requires a [Sensor](#sensor) to send data to the certification test endpoint using this form of transport. A [Sensor](#sensor) MAY employ other methods to communicate with an [Endpoint](#endpoint).

Every message sent by a [Sensor](#sensor) MUST consist of a JSON representation of a single Caliper [Envelope](#envelope).

For transport security and authentication, a [Sensor](#sensor) SHOULD:

* Use HTTPS to secure the transport between the Sensor and receiving endpoint.
* Support message authentication using the Authorization Request Header Field (as described in [RFC 6750, Section 2.1](https://tools.ietf.org/html/rfc6750#section-2); in this case, the `b64token` credential sent by the Sensor MUST be one the [Endpoint](#endpoint) can validate, but the credential MAY be opaque to the [Sensor](#sensor) itself.

A [Sensor](#sensor) MAY support additional modes of transport security and authentication; the certification tests for Caliper sensors require the [Sensor](#sensor) to send data to the certification service using HTTPS and a bearer token credential consistent with [RFC 6750](#rfc6750).

When sending messages to an [Endpoint](#endpoint), a Caliper [Sensor](#sensor) SHOULD indicate that the message payload has the `application/ld+json` IANA media-type, and MAY indicate instead that the message has the `application/json` IANA media-type (in the case, for example, that a Caliper [Endpoint](#endpoint) reports that it cannot process the `application/ld+json` media type).

<a name="endpoint" />

### 4.4 Endpoint

A Caliper endpoint MUST at a minimum be capable of communicating with a [Sensor](#sensor) via the conventional HTTP POST request method; current Caliper certification tests require that the endpoint receive data from the IMS certification suite using this form of transport. Caliper endpoints MAY use other methods to receive data from sensors.

For transport and security and authentication, Caliper sensors SHOULD:

* Use HTTPS to secure the transport between itself and sensors, and if so, MUST provide a valid HTTP Certificate.
* Support message authentication using the Authorization Request Header Field (as described in [RFC 6750, Section 2.1](https://tools.ietf.org/html/rfc6750#section-2); in this case, the `b64token` credential sent by the sensor MUST be one the Endpoint can validate, but the credential MAY be opaque to the sensor itself.

Caliper endpoints MAY support additional modes of transport security and authentication; the certification tests for Caliper endpoints require the endpoint receive data from the certification service using HTTPS and a bearer token credential consistent with [RFC 6750](#rfc6750).

<a name="endpointResponses" />

### 4.5 Endpoint HTTPS responses

When using HTTPS as the transport, the Caliper Endpoint MUST conform to these points of response behaviour. Caliper Endpoint implementers should bear in mind that the Caliper Sensors sending them messages may not be in a position to perform sophisticated error handling.

To signal to the Sensor that it has received the Sensor's message, and no error state pertains (see following), the Endpoint MUST reply with a `2xx` series success. The Endpoint SHOULD use the `200 OK` response, but it MAY instead choose to send a `201 Created` response (to indicate successful receipt and persistence of the Sensor message's contained data payload) or a `202 Accepted` response (to indicate successful acceptance of the Caliper Envelope and queueing for further processing). The body of a successful response SHOULD be empty.

If the Sensor sends a malformed Caliper Envelope (it does not contain `sensor`, `sendTime`, and `dataVersion`, and `data` properties, of the required form), the Endpoint SHOULD reply with a `400 Bad Request` response. (Note that the Endpoint SHOULD NOT send this response if the envelope contains a `dataVersion` value, but it's one that the endpoint cannot support: in this case, the Endpoint SHOULD send a `422 Unprocessable Entity` response instead.)

If the Sensor sends a message with a content-type other than `application/json` or `application/ld+json`, the Endpoint SHOULD reply with a `415 Unsupported Media Type` response.

If the Sensor sends a message without an Authorization Request Header Field of the suggested form, or if the Sensor sends a token credential that the Endpoint is unable to validate or determine has sufficient privilege to submit Caliper data, the Endpoint SHOULD reply with a `401 Unauthorized` response.

The Endpoint MAY respond to Sensor messages with other standard HTTP status codes to indicate result disposition of varying kinds.

If the Endpoint implementer wants the Endpoint to communicate more detailed information about problem states when receiving messages, the Endpoint SHOULD use the standard method for reporting problem details described in [RFC 7807, Problem Details for HTTP APIs](https://tools.ietf.org/html/rfc7807).

<a name="actions"/>
   
## 5.0 Appendix A. Actions
Caliper includes a vocabulary of actions for describing learning interactions. Each action [Term](#termdef) is based on the past-tense form of an English (en-US) verb.  An action [Term](#termdef) can also indicate a change in a particular characteristic of the `object` (e.g., resolution, size, speed, volume).  Each action [Term](#termdef) is mapped to a persistent [IRI](#iriDef) listed in the external IMS Caliper [Context](http://purl.imsglobal.org/ctx/caliper/v1p1).  Each action is also linked to a brief definition ("gloss") derived in whole or in part from Princeton University's WordNet® project in order to eliminate ambiguity and aid natural language processing.
 
 Each Caliper [Event](#event) type supports one one or more of the actions listed below.  The [Event](#event) `action` property string value MUST be set to the appropriate [Term](#termDef). Only one action may be specified per [Event](#event).
 
 **TODO change `action` string value requirement to SHOULD for Term MAY for IRI?**

| Term | IRI | WordNet Gloss |
| :--- | :-- | ------------- |
| <a name="abandoned" />Abandoned | [http://purl.imsglobal.org/vocab/caliper/v1/action#Abandoned](http://purl.imsglobal.org/vocab/caliper/v1/action#Abandoned) | [forsake, leave behind](http://wordnet-rdf.princeton.edu/wn31/202232813-v) |
| <a name="activated" />Activated | [http://purl.imsglobal.org/vocab/caliper/v1/action#Activated](http://purl.imsglobal.org/vocab/caliper/v1/action#Activated) | [make active or more active](http://wordnet-rdf.princeton.edu/wn31/200191014-v) |
| <a name="added" />Added | [http://purl.imsglobal.org/vocab/caliper/v1/action#Added](http://purl.imsglobal.org/vocab/caliper/v1/action#Added) | [make an addition (to); join or combine or unite with others; increase the quality, quantity, size or scope of](http://wordnet-rdf.princeton.edu/wn31/200182551-v) |
| <a name="attached" />Attached | [http://purl.imsglobal.org/vocab/caliper/v1/action#Attached](http://purl.imsglobal.org/vocab/caliper/v1/action#Attached) | [cause to be attached](http://wordnet-rdf.princeton.edu/wn31/201299048-v) |
| <a name="bookmarked" />Bookmarked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Bookmarked](http://purl.imsglobal.org/vocab/caliper/v1/action#Bookmarked) | An [IRI](#iriDef) that marks a location of interest in a DigitalResource that is recorded for later retrieval.  |
| <a name="changedResolution" />ChangedResolution | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedResolution](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedResolution) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of [the number of pixels per square inch on a computer-generated display](http://wordnet-rdf.princeton.edu/wn31/111526370-n) |
| <a name="changedSize" />ChangedSize | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSize](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSize) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of [the physical magnitude of something](http://wordnet-rdf.princeton.edu/wn31/105106204-n) |
| <a name="changedSpeed" />ChangedSpeed | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSpeed](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSpeed) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of the [rate at which something happens](http://wordnet-rdf.princeton.edu/wn31/105065291-n) |
| <a name="changedVolume" />ChangedVolume | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedVolume](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedVolume) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of [the magnitude of sound &#40;usually in a specified direction&#41;](http://wordnet-rdf.princeton.edu/wn31/104997456-n) |
| <a name="classified" />Classified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Classified](http://purl.imsglobal.org/vocab/caliper/v1/action#Classified) | [assign to a class or kind](http://wordnet-rdf.princeton.edu/wn31/200741667-v) |
| <a name="closedPopout" />ClosedPopout | [http://purl.imsglobal.org/vocab/caliper/v1/action#ClosedPopout](http://purl.imsglobal.org/vocab/caliper/v1/action#ClosedPopout) | [close or shut](http://wordnet-rdf.princeton.edu/wn31/201349660-v) a video popout |
| <a name="commented" />Commented | [http://purl.imsglobal.org/vocab/caliper/v1/action#Commented](http://purl.imsglobal.org/vocab/caliper/v1/action#Commented) | [make or write a comment on](http://wordnet-rdf.princeton.edu/wn31/201060446-v) |
| <a name="completed" />Completed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Completed](http://purl.imsglobal.org/vocab/caliper/v1/action#Completed) | [come or bring to a finish or an end](http://wordnet-rdf.princeton.edu/wn31/200485097-v) |
| <a name="created" />Created | [http://purl.imsglobal.org/vocab/caliper/v1/action#Created](http://purl.imsglobal.org/vocab/caliper/v1/action#Created) | [make or cause to be or to become](http://wordnet-rdf.princeton.edu/wn31/201620211-v) |
| <a name="deactivated" />Deactivated | [http://purl.imsglobal.org/vocab/caliper/v1/action#Deactivated](http://purl.imsglobal.org/vocab/caliper/v1/action#Deactivated) | [make inactive](http://wordnet-rdf.princeton.edu/wn31/200191849-v); inverse of activated |
| <a name="deleted" />Deleted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted](http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted) | [wipe out digitally](http://wordnet-rdf.princeton.edu/wn31/201001860-v) |
| <a name="described" />Described | [http://purl.imsglobal.org/vocab/caliper/v1/action#Described](http://purl.imsglobal.org/vocab/caliper/v1/action#Described) | [give a description of](http://wordnet-rdf.princeton.edu/wn31/200989103-v) |
| <a name="disabledClosedCaptioning" />DisabledClosedCaptioning | [http://purl.imsglobal.org/vocab/caliper/v1/action#DisabledClosedCaptioning](http://purl.imsglobal.org/vocab/caliper/v1/action#DisabledClosedCaptioning) | [render unable to perform](http://wordnet-rdf.princeton.edu/wn31/200513267-v) the visual display of a textual transcription of audio output |
| <a name="disliked" />Disliked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Disliked](http://purl.imsglobal.org/vocab/caliper/v1/action#Disliked) | [have or feel a dislike or distaste for](http://wordnet-rdf.princeton.edu/wn31/201780648-v); inverse of liked |
| <a name="enabledClosedCaptioning" />EnabledClosedCaptioning | [http://purl.imsglobal.org/vocab/caliper/v1/action#EnabledClosedCaptioning](http://purl.imsglobal.org/vocab/caliper/v1/action#EnabledClosedCaptioning) | [render capable or able](http://wordnet-rdf.princeton.edu/wn31/200513958-v) the visual display of a textual transcription of audio output |
| <a name="ended" />Ended | [http://purl.imsglobal.org/vocab/caliper/v1/action#Ended](http://purl.imsglobal.org/vocab/caliper/v1/action#Ended) | [bring to an end or halt](http://wordnet-rdf.princeton.edu/wn31/200353480-v) |
| <a name="enteredFullscreen" />EnteredFullScreen | [http://purl.imsglobal.org/vocab/caliper/v1/action#EnteredFullscreen](http://purl.imsglobal.org/vocab/caliper/v1/action#EnteredFullscreen) | [to come or go into](http://wordnet-rdf.princeton.edu/wn31/202020375-v) a view mode that utilizes all the available display surface of a screen |
| <a name="exitedFullscreen" />ExitedFullScreen | [http://purl.imsglobal.org/vocab/caliper/v1/action#ExitedFullscreen](http://purl.imsglobal.org/vocab/caliper/v1/action#ExitedFullscreen) | [move out of or depart from](http://wordnet-rdf.princeton.edu/wn31/202019450-v) a view mode that utilizes all the available display surface of a screen |
| <a name="forwardedTo" />ForwardedTo | [http://purl.imsglobal.org/vocab/caliper/v1/action#ForwardedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#ForwardedTo) | [send or ship onward](http://wordnet-rdf.princeton.edu/wn31/201959367-v) |
| <a name="graded" />Graded | [http://purl.imsglobal.org/vocab/caliper/v1/action#Graded](http://purl.imsglobal.org/vocab/caliper/v1/action#Graded) | [assign a grade or rank to, according to one's evaluation](http://wordnet-rdf.princeton.edu/wn31/200659399-v) |
| <a name="hid" />Hid | [http://purl.imsglobal.org/vocab/caliper/v1/action#Hid](http://purl.imsglobal.org/vocab/caliper/v1/action#Hid) |[prevent from being seen or discovered](http://wordnet-rdf.princeton.edu/wn31/202149298-v) |
| <a name="highlighted" />Highlighted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Highlighted](http://purl.imsglobal.org/vocab/caliper/v1/action#Highlighted) | [move into the foreground to make more visible or prominent](http://wordnet-rdf.princeton.edu/wn31/200515150-v) |
| <a name="identified" />Identified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Identified](http://purl.imsglobal.org/vocab/caliper/v1/action#Identified) | [recognize as being; establish the identity of someone or something](http://wordnet-rdf.princeton.edu/wn31/200620568-v) |
| <a name="jumpedTo" />JumpedTo | [http://purl.imsglobal.org/vocab/caliper/v1/action#JumpedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#JumpedTo) | [pass abruptly from one state or topic to another](http://wordnet-rdf.princeton.edu/wn31/200561468-v) |
| <a name="liked" />Liked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Liked](http://purl.imsglobal.org/vocab/caliper/v1/action#Liked) | [be fond of](http://wordnet-rdf.princeton.edu/wn31/201780873-v) |
| <a name="linked" />Linked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Linked](http://purl.imsglobal.org/vocab/caliper/v1/action#Linked) | [connect, fasten, or put together two or more pieces](http://wordnet-rdf.princeton.edu/wn31/201357376-v) |
| <a name="loggedIn" />LoggedIn | [http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn) | [enter a computer or software application](http://wordnet-rdf.princeton.edu/wn31/202253955-v) |
| <a name="loggedIn" />LoggedOut | [http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut) | [exit a computer or software application](http://wordnet-rdf.princeton.edu/wn31/202254101-v) |
| <a name="markedAsRead" />MarkedAsRead | [http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead) | [mark: designate as if by a mark](http://wordnet-rdf.princeton.edu/wn31/200923709-v), [read: interpret something that is written or printed](http://wordnet-rdf.princeton.edu/wn31/200626756-v) |
| <a name="markedAsUnread" />MarkedAsUnread | [http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread) | inverse of markedAsRead |
| <a name="modified" />Modified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Modified](http://purl.imsglobal.org/vocab/caliper/v1/action#Modified) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) |
| <a name="muted" />Muted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Muted](http://purl.imsglobal.org/vocab/caliper/v1/action#Muted) | [deaden (a sound or noise)](http://wordnet-rdf.princeton.edu/wn31/mute-v) |
| <a name="navigated to" />NavigatedTo | [http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo) | [direct the course; determine the direction of travelling](http://wordnet-rdf.princeton.edu/wn31/201935739-v) |
| <a name="openedPopout" />OpenedPopout | [http://purl.imsglobal.org/vocab/caliper/v1/action#OpenedPopout](http://purl.imsglobal.org/vocab/caliper/v1/action#OpenedPopout) | [start to operate or function or cause to start operating or functioning](http://wordnet-rdf.princeton.edu/wn31/202431018-v) a video popout |
| <a name="paused" />Paused | [http://purl.imsglobal.org/vocab/caliper/v1/action#Paused](http://purl.imsglobal.org/vocab/caliper/v1/action#Paused) | [cease an action temporarily](http://wordnet-rdf.princeton.edu/wn31/200781106-v) |
| <a name="posted" />Posted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Posted](http://purl.imsglobal.org/vocab/caliper/v1/action#Posted) | [to cause to be directed or transmitted to another place](http://wordnet-rdf.princeton.edu/wn31/201033289-v)  |
| <a name="questioned" />Questioned | [http://purl.imsglobal.org/vocab/caliper/v1/action#Questioned](http://purl.imsglobal.org/vocab/caliper/v1/action#Questioned) | [pose a question](http://wordnet-rdf.princeton.edu/wn31/200786670-v) |
| <a name="ranked" />Ranked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Ranked](http://purl.imsglobal.org/vocab/caliper/v1/action#Ranked) | [assign a rank or rating to](http://wordnet-rdf.princeton.edu/wn31/200659723-v) |
| <a name="recommended" />Recommended | [http://purl.imsglobal.org/vocab/caliper/v1/action#Recommended](http://purl.imsglobal.org/vocab/caliper/v1/action#Recommended) | [express a good opinion of](http://wordnet-rdf.princeton.edu/wn31/200884469-v) |
| <a name="removed" />Removed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Removed](http://purl.imsglobal.org/vocab/caliper/v1/action#Removed) | [remove from sight](http://wordnet-rdf.princeton.edu/wn31/200181704-v) |
| <a name="reset" />Reset | [http://purl.imsglobal.org/vocab/caliper/v1/action#Reset](http://purl.imsglobal.org/vocab/caliper/v1/action#Reset) | [set anew](http://wordnet-rdf.princeton.edu/wn31/200949623-v) |
| <a name="restarted" />Restarted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Restarted](http://purl.imsglobal.org/vocab/caliper/v1/action#Restarted) | [take up or begin anew](http://wordnet-rdf.princeton.edu/wn31/200350758-v)|
| <a name="resumed" />Resumed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Resumed](http://purl.imsglobal.org/vocab/caliper/v1/action#Resumed) | [take up or begin anew](http://wordnet-rdf.princeton.edu/wn31/200350758-v) |
| <a name="retrieved" />Retrieved | [http://purl.imsglobal.org/vocab/caliper/v1/action#Retrieved](http://purl.imsglobal.org/vocab/caliper/v1/action#Retrieved) | [obtain or retrieve from a storage device; as of information on a computer](http://wordnet-rdf.princeton.edu/wn31/202253616-v) |
| <a name="reviewed" />Reviewed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Reviewed](http://purl.imsglobal.org/vocab/caliper/v1/action#Reviewed) | [appraise critically](http://wordnet-rdf.princeton.edu/wn31/200857194-v) |
| <a name="rewound" />Rewound | [http://purl.imsglobal.org/vocab/caliper/v1/action#Rewound](http://purl.imsglobal.org/vocab/caliper/v1/action#Rewound) | [wind up again](http://wordnet-rdf.princeton.edu/wn31/201524927-v)|
| <a name="searched" />Searched | [http://purl.imsglobal.org/vocab/caliper/v1/action#Searched](http://purl.imsglobal.org/vocab/caliper/v1/action#Searched) | [try to locate or discover, or try to establish the existence of](http://wordnet-rdf.princeton.edu/wn31/201318273-v) |
| <a name="shared" />Shared | [http://purl.imsglobal.org/vocab/caliper/v1/action#Shared](http://purl.imsglobal.org/vocab/caliper/v1/action#Shared) | [communicate](http://wordnet-rdf.princeton.edu/wn31/201065952-v) |
| <a name="showed" />Showed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Showed](http://purl.imsglobal.org/vocab/caliper/v1/action#Showed) | [make visible or noticeable](http://wordnet-rdf.princeton.edu/wn31/202141597-v) |
| <a name="skipped" />Skipped | [http://purl.imsglobal.org/vocab/caliper/v1/action#Skipped](http://purl.imsglobal.org/vocab/caliper/v1/action#Skipped) | [bypass](http://wordnet-rdf.princeton.edu/wn31/200618188-v) |
| <a name="started" />Started | [http://purl.imsglobal.org/vocab/caliper/v1/action#Started](http://purl.imsglobal.org/vocab/caliper/v1/action#Started) | [set in motion, cause to start](http://wordnet-rdf.princeton.edu/wn31/200349400-v) |
| <a name="submitted" />Submitted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Submitted](http://purl.imsglobal.org/vocab/caliper/v1/action#Submitted) | [hand over formally](http://wordnet-rdf.princeton.edu/wn31/202267560-v) |
| <a name="subscribed" />Subscribed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed) | [ receive or obtain regularly](http://wordnet-rdf.princeton.edu/wn31/202214527-v) |
| <a name="tagged" />Tagged | [http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged](http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged) | [attach a tag or label to](http://wordnet-rdf.princeton.edu/wn31/201591414-v) |
| <a name="timedOut" />TimedOut | [http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut](http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut) | Cancellation of a user session after a predetermined time interval has occurred without activity. |
| <a name="unmuted" />Unmuted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Unmuted](http://purl.imsglobal.org/vocab/caliper/v1/action#Unmuted) | inverse of muted |
| <a name="unsubscribed" />Unsubscribed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed) | inverse of subscribed |
| <a name="used" />Used | [http://purl.imsglobal.org/vocab/caliper/v1/action#Used](http://purl.imsglobal.org/vocab/caliper/v1/action#Used) | interact with a tool in a manner the tool creator intends as a learning activity |
| <a name="viewed" />Viewed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed](http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed) |[look at carefully; study mentally](http://wordnet-rdf.princeton.edu/wn31/202134765-v) |

<a name="events" />

## 6.0 Appendix B. Event Types

<a name="annotationEvent" />

### 6.1 AnnotationEvent
The Caliper [AnnotationEvent](#annotationEvent) models the annotating of digital content.  The resulting [Annotation](#annotation) is also described and is subtyped for greater type specificity.

#### Supported actions
 [Bookmarked](#bookmarked), [Highlighted](#highlighted), [Shared](#shared), [Tagged](#tagged)
 
#### Deprecated actions
[Attached](#attached), [Classified](#classified),  [Commented](#commented), [Described](#described), [Disliked](#disliked), [Identified](#identified), [Liked](#liked), [Linked](#linked), [Questioned](#questioned), [Ranked](#ranked), [Recommended](#recommended), [Replied](#replied), [Subscribed](#subscribed)

#### Generated annotations
[Annotation](#annotation), [BookmarkAnnotation](#bookmarkAnnotation), [HighlightAnnotation](#highlightAnnotation), [SharedAnnotation](#sharedAnnotation), [TagAnnotation](#tagAnnotation)
 
#### Properties
[AnnotationEvent](#annotationEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *AnnotationEvent*. | Required |
| actor | [Person](#person) | the [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | String | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the supported action terms listed above.  Only one `action` term may be specified per [Event](#event).  Deprecated actions SHOULD NOT be utilized. | Required |
| object | [DigitalResource](#digitalResource) | The annotated [DigitalResource](#digitalResource) that constitutes the `object` of the interaction MUST be specified.  [DigitalResource](#digitalResource) is a generic type that is subtyped for greater type specificity.  Utilize [DigitalResource](#digitalResource) only if no suitable subtype exists to represent the `object`. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Frame](#frame) | A [Frame](#frame) that represents a particular segment or location within the `object`. | Optional |
| generated | [Annotation](#annotation) | the `generated` [Annotation](#annotation) SHOULD be specified.  Note that Annotation is a generic type that is subtyped for greater type specificity.  Utilize [Annotation](#annotation) only if no suitable subtype exists to represent the `generated` object. | Recommended |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: AnnotationEvent (bookmarked)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "AnnotationEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Bookmarked",
  "object": {
    "id": "https://example.edu/etexts/201.epub",
    "type": "Document",
    "name": "IMS Caliper Implementation Guide",
    "version": "1.1"
  },
  "generated": {
    "id": "https://example.edu/users/554433/etexts/201/bookmarks/1",
    "type": "BookmarkAnnotation",
    "annotator": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "annotated": {
      "id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!/4[body01]/10[para05]/1:20)",
      "type": "Chapter"
    },
    "bookmarkNotes": "Caliper profiles model discrete learning activities or supporting activities that enable learning.",
    "dateCreated": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "name": "ePub Reader",
    "version": "1.2.3"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "d4618c23-d612-4709-8d9a-478d87808067"
}
```
	
<a name="assessmentEvent" />

### 6.2 AssessmentEvent
The Caliper [AssessmentEvent](#assessmentEvent) models learner interactions with assessments instruments such as online tests or quizzes.  

#### Supported actions
[Started](#started), [Paused](#paused), [Restarted](#restarted), [Submitted](#submitted)

#### Properties
[AssessmentEvent](#assessmentEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *AssessmentEvent*. | Required |
| actor | [Person](#person) | the [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | the action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the supported action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [Assessment](#assessment), [Attempt](#attempt) | For [Started](#started), [Paused](#paused) and [Restarted](#restarted) actions the [Assessment](#assessment) constitutes the `object` of the interaction and MUST be specified.  For a [Submitted](#submitted) action the actor's [Attempt](#attempt) is the `object` and MUST be specified. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Entity](#entity) | An [Entity](#entity) that represents a particular segment or location within the `object`. | Optional |
| generated | [Assessment](#assessment), [Attempt](#attempt) | For [Started](#started), [Paused](#paused) and [Restarted](#restarted) actions an [Attempt](#attempt) SHOULD be specified in order to record a [count](#count) of the number of times the `actor` has interacted with the [Assessment](#assessment). | Recommended |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: AssessmentEvent (started)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "AssessmentEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Started",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "type": "Assessment",
    "name": "Quiz One",
    "dateToStartOn": "2016-11-14T05:00:00.000Z",
    "dateToSubmit": "2016-11-18T11:59:59.000Z",
    "maxAttempts": 2,
    "maxSubmits": 2,
    "maxScore": 25.0,
    "version": "1.0"
  },
  "generated": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "type": "Assessment"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:15:00.000Z",
    "startedAtTime": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "27734504-068d-4596-861c-2315be33a2a2"
}
```

#### Example: AssessmentEvent (submitted)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "AssessmentEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Submitted",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "type": "Assessment",
      "name": "Quiz One",
      "dateToStartOn": "2016-11-14T05:00:00.000Z",
      "dateToSubmit": "2016-11-18T11:59:59.000Z",
      "maxAttempts": 2,
      "maxSubmits": 2,
      "maxScore": 25.0,
      "version": "1.0"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:15:00.000Z",
    "startedAtTime": "2016-11-15T10:15:00.000Z",
    "endedAtTime": "2016-11-15T10:25:30.000Z",
    "duration": "PT10M30S"
  },
  "eventTime": "2016-11-15T10:25:30.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "dad88464-0c20-4a19-a1ba-ddf2f9c3ff33"
}
```

<a name="assessmentItemEvent" />

### 6.3 AssessmentItemEvent
The Caliper [AssessmentItemEvent](#assessmentItemEvent) models a learner's interaction with an individual [AssessmentItem](#assessmentItem).  

#### Supported actions
[Started](#started), [Skipped](#skipped), [Completed](#completed)

#### Generated responses
[Response](#response), [FillinBlankResponse](#fillinBlankResponse), [MultipleChoiceResponse](#multipleChoiceResponse), [MultipleResponseResponse](#multipleResponseResponse), [SelectTextResponse](#selectTextResponse), [TrueFalseResponse](#trueFalseResponse)

#### Properties
[AssessmentItemEvent](#assessmentItemEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *AssessmentItemEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [AssessmentItem](#assessmentItem), [Attempt](#attempt) | For [Started](#started) and [Skipped](#skipped) actions the [AssessmentItem](#assessmentItem) constitutes the `object` of the interaction and MUST be specified.  For a [Completed](#completed) action the actor's [Attempt](#attempt) is the `object` and MUST be specified. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Entity](#entity) | An [Entity](#entity) that represents a particular segment or location within the `object`. | Optional |
| generated | [Attempt](#attempt), [Response](#response) | For [Started](#started) and [Skipped](#skipped) actions, the [Attempt](#attempt) constitutes the `object` and SHOULD be specified.  For a [completed](#completed) action a `generated` [Response](#response) MAY be specified.  Note that [Response](#response) is a generic type that is subtyped for greater type specificity.  Utilize [Response](#response) only if no suitable subtype exists to represent the `generated` object. | Recommended |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [AssessmentItem](#assessmentItem) | The previous [AssessmentItem](#assessmentItem) attempted MAY be specified as the `referrer`. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: AssessmentItem (started)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "AssessmentItemEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Started",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
    "type": "AssessmentItem",
    "name": "Assessment Item 3",
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "type": "Assessment"
    },
    "dateToStartOn": "2016-11-14T05:00:00.000Z",
    "dateToSubmit": "2016-11-18T11:59:59.000Z",
    "maxAttempts": 2,
    "maxSubmits": 2,
    "maxScore": 1.0,
    "isTimeDependent": false,
    "version": "1.0"
    },
  "generated": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "type": "AssessmentItem"
    },
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
      "type": "Attempt"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:15:00.000Z",
    "startedAtTime": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "1b557176-ba67-4624-b060-6bee670a3d8e"
}
```

#### Example: AssessmentItem (completed)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "AssessmentItemEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Completed",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "type": "AssessmentItem",
      "name": "Assessment Item 3",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment"
      }
    },
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
      "type": "Attempt"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:15:02.000Z",
    "startedAtTime": "2016-11-15T10:15:02.000Z",
    "endedAtTime": "2016-11-15T10:15:12.000Z"
  },
  "generated": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/responses/1",
    "type": "FillinBlankResponse",
    "attempt": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
      "type": "Attempt"
    },
    "dateCreated": "2016-11-15T10:15:12.000Z",
    "startedAtTime": "2016-11-15T10:15:02.000Z",
    "endedAtTime": "2016-11-15T10:15:12.000Z",
    "values": [ "subject", "object", "predicate" ]
  },
  "eventTime": "2016-11-15T10:15:12.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "e5891791-3d27-4df1-a272-091806a43dfb"
}
```

<a name="assignableEvent" />

### 6.4 AssignableEvent
TODO The Caliper [AssignableEvent](#assignableEvent) models . . . .

#### Supported actions
[Activated](#activated), [Deactivated](#deactivated), [Started](#started), [Completed](#completed), [Reviewed](#reviewed)

#### Deprecated actions
[Abandoned](#abandoned), [Hid](#hid), [Showed](#showed)

#### Properties
[AssignableEvent](#assignableEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *AssignableEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above. Only one `action` [Term](#termDef) may be specified per [Event](#event).  Deprecated actions SHOULD NOT be utilized. | Required | 
| object | [AssignableDigitalResource](#assignableDigitalResource) | The [AssignableDigitalResource](#assignableDigitalResource) that constitutes the `object` of the interaction MUST be specified.  [AssignableDigitalResource](#assignableDigitalResource) is a generic type that is subtyped for greater type specificity.  Utilize [AssignableDigitalResource](#assignableDigitalResource) only if no suitable subtype exists to represent the `object`. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Frame](#frame) | A [Frame](#frame) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: AssignableEvent (activated)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "AssignableEvent",
  "actor": {
    "id": "https://example.edu/users/112233",
    "type": "Person"
  },
  "action": "Activated",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "type": "Assessment",
    "name": "Quiz One",
    "dateCreated": "2016-08-01T06:00:00.000Z",
    "dateModified": "2016-09-02T11:30:00.000Z",
    "datePublished": "2016-11-12T10:10:00.000Z",
    "dateToActivate": "2016-11-12T10:15:00.000Z",
    "dateToStartOn": "2016-11-14T05:00:00.000Z",
    "dateToSubmit": "2016-11-18T11:59:59.000Z",
    "maxAttempts": 2,
    "maxSubmits": 2,
    "maxScore": 25.0,
    "version": "1.0"
  },
  "eventTime": "2016-11-12T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/112233",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Instructor" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/f095bbd391ea4a5dd639724a40b606e98a631823",
    "type": "Session",
    "startedAtTime": "2016-11-12T10:00:00.000Z"
  },
  "uuid": "2635b9dd-0061-4059-ac61-2718ab366f75"
}
```

<a name="forumEvent" />

### 6.5 ForumEvent

TODO The Caliper [ForumEvent](#forumEvent) models . . . .

#### Supported actions
[Subscribed](#subscribed), [Unsubscribed](#unsubscribed)

#### Properties
[ForumEvent](#forumEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *ForumEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object| [Forum](#forum) | The [Forum](#forum) that comprises the `object` of this interaction MUST be specified. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Entity](#entity) | An [Entity](#entity) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: ForumEvent (subscribed)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "ForumEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Subscribed",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
    "type": "Forum",
    "name": "Caliper Forum",
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "dateCreated": "2016-09-14T11:00:00.000Z"
  },
  "eventTime": "2016-11-15T10:16:00.000Z",
  "edApp": {
    "id": "https://example.edu/forums",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "a2f41f9c-d57d-4400-b3fe-716b9026334e"
}
```

<a name="mediaEvent" />

### 6.6 MediaEvent
TODO The Caliper [MediaEvent](#mediaEvent) models . . . .

TODO   
* Should MediaLocation be the object or the target of the interaction?
* Should ImageObject be included in this event (ViewEvent appears more appropriate)?

#### Supported actions
[Started](#started), [Paused](#paused), [Resumed](#resumed), [Ended](#ended), [ForwardedTo](#forwardedTo), [JumpedTo](#jumpedTo), [Rewound](#rewound), [ChangedResolution](#changedResolution), [ChangedSize](#changedSize), [ChangedSpeed](#changedSpeed), [ChangedVolume](#changedVolume), [EnabledClosedCaptioning](#enabledClosedCaptioning), [DisabledClosedCaptioning](#disabledClosedCaptioning), [EnteredFullScreen](#enteredFullScreen), [ExitedFullScreen](#exitedFullScreen), [Muted](#muted), [Unmuted](#unmuted), [OpenedPopout](#openedPopout), [ClosedPopout](#closedPopout)

#### Properties
[MediaEvent](#mediaEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *MediaEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` term may be specified per [Event](#event). | Required |
| object | [MediaObject](#mediaObject) | The [MediaObject](#mediaObject) that constitutes the `object` of the interaction MUST be specified.  [MediaObject](#mediaObject) is a generic type that is subtyped for greater type specificity.  Utilize [MediaObject](#mediaObject) only if no suitable subtype exists to represent the `object`. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [MediaLocation](#mediaLocation) | If the `object` is an [AudioObject](#audioObject) or [VideoObject](#videoObject) a [MediaLocation](#mediaLocation) SHOULD be specified in order to provide the [currentTime](#currentTime) in the audio or video stream that marks the action.  The value MUST be an ISO 8601 formatted duration, e.g., "PT30M54S". | Recommended |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: MediaEvent (paused)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "MediaEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Paused",
  "object": {
    "id": "https://example.edu/UQVK-dsU7-Y",
    "type": "VideoObject",
    "name": "Information and Welcome",
    "mediaType": "video/ogg",
    "duration": "PT20M20S"
  },
  "target": {
    "id": "https://example.edu/UQVK-dsU7-Y?t=321",
    "type": "MediaLocation",
    "currentTime": "PT05M21S"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu/player",
    "type": "SoftwareApplication"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "956b4a02-8de0-4991-b8c5-b6eebb6b4cab"
}
```

<a name="messageEvent" />

### 6.7 MessageEvent
The Caliper [MessageEvent](#messageEvent) describes a [Person](#person) posting a [Message](#message) or marking a post as either read or unread.

#### Supported actions
[posted](#posted), [markedAsRead](#markedAsRead), [markedAsUnRead](#markedAsUnRead)

#### Properties
[MessageEvent](#messageEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *MessageEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | the action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [Message](#Message) | The [Message](#Message) that constitutes the `object` of the interaction MUST be specified.  If the `object` represents a [Message](#Message) posted in reply to a previous post, the prior post prompting the [Message](#Message) SHOULD be referenced using the [Message](#Message) `replyTo` property. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Entity](#entity) | An [Entity](#entity) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: MessageEvent (posted)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "MessageEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Posted",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/2",
    "type": "Message",
    "creators": [
      {
        "id": "https://example.edu/users/554433",
        "type": "Person"
      }
    ],
    "body": "Are the Caliper Sensor reference implementations production-ready?",
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1",
      "type": "Thread",
      "name": "Caliper Adoption",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2",
        "type": "Forum",
        "name": "Caliper Forum"
      }
    },
    "dateCreated": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu/forums",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "0d015a85-abf5-49ee-abb1-46dbd57fe64e"
}
```

#### Example: MessageEvent (posted reply)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "MessageEvent",
  "actor": {
    "id": "https://example.edu/users/778899",
    "type": "Person"
  },
  "action": "Posted",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/3",
    "type": "Message",
    "creators": [
      {
        "id": "https://example.edu/users/778899",
        "type": "Person"
      }
    ],
    "replyTo": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/2",
      "type": "Message"
    },
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1",
      "type": "Thread",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2",
        "type": "Forum"
      }
    },
    "dateCreated": "2016-11-15T10:15:30.000Z"
  },
  "eventTime": "2016-11-15T10:15:30.000Z",
  "edApp": {
    "id": "https://example.edu/forums",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/778899",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1d6fa9adf16f4892650e4305f6cf16610905cd50",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:12:00.000Z"
  },
  "uuid": "aed54386-a3fb-45ff-90f9-a35d3daaf031"
}
```

<a name="navigationEvent" />

### 6.8 NavigationEvent
The Caliper [NavigationEvent](#navigationEvent) models an actor traversing a network of digital resources.

#### Supported actions
[NavigatedTo](#navigatedTo)

#### Properties
[NavigationEvent](#navigationEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *NavigationEvent*. |Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [DigitalResource](#digitalResource), [SoftwareApplication](#softwareApplication)| The [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the `object` of the interaction MUST be specified. Note that [DigitalResource](#digitalResource)  is a generic type that is subtyped for greater type specificity.  Utilize [DigitalResource](#digitalResource)  only if no suitable subtype exists to represent the `object`. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Frame](#frame) | A [Frame](#frame) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [DigitalResource](#digitalResource), [SoftwareApplication](#softwareApplication) | The [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context SHOULD be specified.  Note that [DigitalResource](#digitalResource)  is a generic type that is subtyped for greater type specificity.  Utilize [DigitalResource](#digitalResource)  only if no suitable subtype exists to represent the `referrer`. | Recommended |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: NavigationEvent (navigated to)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "NavigationEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "NavigatedTo",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/pages/2",
    "type": "WebPage",
    "name": "Learning Analytics Specifications",
    "description": "Overview of Learning Analytics Specifications with particular emphasis on IMS Caliper.",
    "dateCreated": "2016-08-01T09:00:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "referrer": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/pages/1",
    "type": "WebPage"
  },
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "ff9ec22a-fc59-4ae1-ae8d-2c9463ee2f8f"
}
```

<a name="outcomeEvent" />

### 6.9 OutcomeEvent
TODO The Caliper [OutcomeEvent](#outcomeEvent) models . . . .

#### Supported actions
[Graded](#graded)

#### Properties
[OutcomeEvent](#outcomeEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *OutcomeEvent*. | Required |
| actor | [Agent](#agent) | A generic [Agent](#agent) or one of its subtypes, typically [Person](#person) or [SoftwareApplication](#softwareApplication), MUST be specified as the `actor`. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [Attempt](#attempt) | The completed [Attempt](#attempt) MUST be specified. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Entity](#entity) | An [Entity](#entity) that represents a particular segment or location within the `object`. | Not Applicable |
| generated | [Result](#result) | The generated [Result](#result) SHOULD be provided. | Recommended |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: OutcomeEvent (graded)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "OutcomeEvent",
  "actor": {
    "id": "https://example.edu/autograder",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "action": "Graded",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "type": "Assessment"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:05:00.000Z",
    "startedAtTime": "2016-11-15T10:05:00.000Z",
    "endedAtTime": "2016-11-15T10:55:12.000Z",
    "duration": "PT50M12S"
  },
  "eventTime": "2016-11-15T10:57:06.000Z",
  "generated": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/results/1",
    "type": "Result",
    "attempt": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
      "type": "Attempt"
    },
    "normalScore": 15.0,
    "totalScore": 15.0,
    "scoredBy": {
      "id": "https://example.edu/autograder",
      "type": "SoftwareApplication"
    },
    "dateCreated": "2016-11-15T10:55:05.000Z"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "uuid": "a50ca17f-5971-47bb-8fca-4e6e6879001d"
}
```
<a name="readingEvent" />

### 6.10 ReadingEvent DEPRECATED

The Caliper [ReadingEvent](#readingEvent) models an actor reading textural content.  ReadingEvent is DEPRECATED and will be removed in a future version of the specification.  It SHOULD NOT be utilized.

#### Supported actions
[NavigatedTo](#navigatedTo), [Searched](#searched), [Viewed](#viewed)

#### Properties
[ReadingEvent](#readingEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *ReadingEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | the action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [DigitalResource](#digitalResource) | The [DigitalResource](#digitalResource) that constitutes the `object` of the interaction MUST be specified.  [DigitalResource](#digitalResource) is a generic type that is subtyped for greater type specificity.  Utilize [DigitalResource](#digitalResource) only if no suitable subtype exists to represent the object. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Frame](#frame) | A [Frame](#frame) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

<a name="sessionEvent" />

### 6.11 SessionEvent
TODO A Caliper [SessionEvent](#sessionEvent) models . . . .

#### Supported actions
[LoggedIn](#loggedIn), [LoggedOut](#loggedOut), [TimedOut](#timedOut)

#### Properties
[SessionEvent](#sessionEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *SessionEvent*. | Required |
| actor | [Agent](#agent) | The [Agent](#agent) who initiated the `action` MUST be specified.  For [LoggedIn](#loggedIn) and [LoggedOut](#loggedOut) actions a [Person](#person) MUST be specified as the `actor`.  For a [TimedOut](#timedOut) action a [SoftwareApplication](#softwareApplication) MUST be specified as the `actor`. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event). | Required |
| object | [Session](#session), [SoftwareApplication](#softwareApplication) | For [LoggedIn](#loggedIn) and [LoggedOut](#loggedOut) actions a [SoftwareApplication](#softwareApplication) MUST be specified as the `object`.  For a [TimedOut](#timedOut) action the [Session](#session) MUST be specified as the object. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [DigitalResource](#digitalResource) | When logging in to a [SoftwareApplication](#softwareApplication), if the actor is attempting to access a particular [DigitalResource](#digitalResource) it MAY be designated as the `target` of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [DigitalResource](#digitalResource), [SoftwareApplication](#softwareApplication) | The [DigitalResource](#digitalResource) or [SoftwareApplication](#softwareApplication) that constitutes the referring context MAY be specified as the `referrer`. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | the relevant user [Session](#session) SHOULD be specified. | Recommended |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: SessionEvent (logged in)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "uuid": "341db3d9-71cc-4081-9423-cbed73cb0179",
  "type": "SessionEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "LoggedIn",
  "object": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "user": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "dateCreated": "2016-11-15T10:00:00.000Z",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "fcd495d0-3740-4298-9bec-1154571dc211"
}
```

#### Example: SessionEvent (logged out)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "uuid": "5fac90a9-531a-41f6-9b8d-7a26e61dcc27",
  "type": "SessionEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "LoggedOut",
  "object": {
    "id": "https://example.edu",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "eventTime": "2016-11-15T11:05:00.000Z",
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "user": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "dateCreated": "2016-11-15T10:00:00.000Z",
    "startedAtTime": "2016-11-15T10:00:00.000Z",
    "endedAtTime": "2016-11-15T11:05:00.000Z",
    "duration": "PT3000S"
  },
  "uuid": "a438f8ac-1da3-4d48-8c86-94a1b387e0f6"
}
```

#### Example: SessionEvent (timed out)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "uuid": "513d4ca1-0ecf-4234-932d-c4cb287884a3",
  "type": "SessionEvent",
  "actor": {
    "id": "https://example.edu",
    "type": "SoftwareApplication"
  },
  "action": "TimedOut",
  "object": {
    "id": "https://example.edu/sessions/7d6b88adf746f0692e2e873308b78c60fb13a864",
    "type": "Session",
    "user": {
      "id": "https://example.edu/users/112233",
      "type": "Person"
    },
    "dateCreated": "2016-11-15T10:15:00.000Z",
    "startedAtTime": "2016-11-15T10:15:00.000Z",
    "endedAtTime": "2016-11-15T11:15:00.000Z",
    "duration": "PT3600S"
  },
  "eventTime": "2016-11-15T11:15:00.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication"
  },
  "uuid": "4e61cf6c-ffbe-45bc-893f-afe7ad4079dc"
}
```

<a name="threadEvent" />

### 6.12 ThreadEvent
TODO A Caliper [ThreadEvent](#threadEvent) models an actor marking a forum thread or topic as either read or unread.  

#### Supported actions
[MarkedAsRead](#markedAsRead), [MarkedAsUnRead](#markedAsUnread)

#### Properties
[ThreadEvent](#threadEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the term *ThreadEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef) may be specified per [Event](#event).  | Required |
| object | The [Thread](#thread) that constitutes the `object` of the interaction MUST be specified. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Entity](#entity) | An [Entity](#entity) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: ThreadEvent (marked as read)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "ThreadEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "MarkedAsRead",
  "object": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1",
    "type": "Thread",
    "name": "Caliper Information Model",
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
      "type": "Forum",
      "name": "Caliper Forum",
      "dateCreated": "2016-11-15T10:15:00.000Z"
    },
    "dateCreated": "2016-11-15T10:16:00.000Z"
  },
  "eventTime": "2016-11-15T10:16:00.000Z",
  "edApp": {
    "id": "https://example.edu/forums",
    "type": "SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "6b20c5ba-301c-4e56-85a0-2f3d9a94c249"
}
```

<a name="toolUseEvent" />

### 6.13 ToolUseEvent
A Caliper [ToolUseEvent](#toolUseEvent) models a [Person](#person) using a learning tool in a way that the tool's creators have determined is an indication of a learning interaction. It's meant to be a fundamental [Event](#event) that tool creators can implement to demonstrate that users are using the tool in the way in which it's intended to be used.

#### Supported actions
[Used](#used)

#### Properties
[ToolUseEvent](#toolUseEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *ToolUseEvent*. | Required |
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef)  may be specified per [Event](#event). | Required |
| object | [SoftwareApplication](#softwareApplication) | The [SoftwareApplication](#softwareApplication) that constitutes  the `object` of the interaction MUST be specified. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that represents a particular capability or feature provided by the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example: ToolUseEvent (used)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "ToolUseEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Used",
  "object": {
    "id": "https://example.edu",
    "type": "SoftwareApplication"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "7e10e4f3-a0d8-4430-95bd-783ffae4d916"
}
```

<a name="viewEvent" />

### 6.14 ViewEvent
A Caliper [ViewEvent](#viewEvent) describes an actor's examination of digital content whenever the activity emphasizes thoughtful observation or study as opposed to the mere retrieval of a resource.

#### Supported actions
[viewed](#viewed)

#### Properties
[ViewEvent](#viewEvent) inherits all properties defined by its superclass [Event](#event). Additional requirements are described below:

| Property | Type | Description | Conformance |
| :------- | :--- | ----------- | :---------: |
| uuid | [UUID](https://tools.ietf.org/html/rfc4122) | A [UUID](https://tools.ietf.org/html/rfc4122) string value that conforms to [RFC 4122](#rfc4122) MUST be generated. | Required | 
| type | [Term](#termDef) | The string value MUST be set to the [Term](#termDef) *ViewEvent* MUST be specified.
| actor | [Person](#person) | The [Person](#person) who initiated the `action` MUST be specified. | Required |
| action | [Term](#termDef) | The action or predicate that binds the `actor` or subject to the `object` MUST be specified.  The value range is limited to the action terms listed above.  Only one `action` [Term](#termDef)  may be specified per [Event](#event). | Required |
| object | [DigitalResource](#digitalResource) | The [DigitalResource](#digitalResource) that constitutes the `object` of the interaction MUST be specified.  [DigitalResource](#digitalResource) is a generic type that is subtyped for greater type specificity.  Utilize [DigitalResource](#digitalResource) only if no suitable subtype exists to represent the object. | Required |
| eventTime | DateTime | A date and time value expressed with millisecond precision that indicates when the [Event](#event) occurred MUST be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC. | Required |
| target | [Frame](#frame) | A [Frame](#frame) that represents a particular segment or location within the `object`. | Optional |
| generated | [Entity](#entity) | An [Entity](#entity) created or generated as a result of the interaction. | Optional |
| edApp | [SoftwareApplication](#softwareApplication) | A [SoftwareApplication](#softwareApplication) that constitutes the application context MAY be specified. | Optional | 
| referrer | [Entity](#entity) | An [Entity](#entity) that represents the referring context MAY be specified. A [SoftwareApplication](#softwareApplication) or [DigitalResource](#digitalResource) will typically constitute the referring context. | Optional |
| group | [Organization](#organization) | An [Organization](#organization) that represents the group context MAY be specified. | Optional | 
| membership | [Membership](#membership) | The relationship between the `actor` and the `group` in terms of roles assigned and current status MAY be specified. | Optional | 
| session | [Session](#session) | The current user [Session](#session) MAY be specified. | Optional |
| federatedSession | [LtiSession](#ltiSession) | If the [Event](#event) occurs within the context of an [LTI](#lti) tool launch, the actor's tool consumer [LtiSession](#ltiSession) MAY be referenced. | Optional | 
| extensions | Array | An ordered collection of objects not defined by the model MAY be specified for a more concise representation of the [Event](#event). | Optional |

#### Example ViewEvent (viewed)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "type": "ViewEvent",
  "actor": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "action": "Viewed",
  "object": {
    "id": "https://example.edu/etexts/200.epub",
    "type": "Document",
    "name": "IMS Caliper Specification",
    "version": "1.1"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "id": "https://example.edu",
    "type": "SoftwareApplication"
  },
  "group": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "type": "Membership",
    "member": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "organization": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    },
    "roles": [ "Learner" ],
    "status": "Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "type": "Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "uuid": "3a9bd869-addc-48b1-80f6-a14b2ff591ed",
  "extensions": [{
    "@context": {
      "id": "@id",
      "type": "@type",
      "example": "http://example.edu/ctx/edu",
      "xsd": "http://www.w3.org/2001/XMLSchema#",
      "ChronJob": "example:ChronJob",
      "job": "example:job",
      "jobTag": { "id": "example:jobTag", "type": "xsd:string" },
      "jobDate": { "id": "example:jobDate", "type": "xsd:dateTime" }
    },
    "job": {
      "id": "https://example.edu/data/jobs/08c1233d-9ba3-40ac-952f-004c47a50ff7",
      "type": "ChronJob",
      "jobTag": "caliper",
      "jobDate": "2016-11-16T01:01:00.000Z"
    }
  }]
}
```

<a name="entities" />

### 7.0 Appendix C. Entity Types

<a name="agent" />

### 7.1 Agent
A Caliper Agent is a generic class that represents an Entity that can initiate or perform an action.  It is analogous to an [foaf:Agent](http://xmlns.com/foaf/spec/#term_Agent).  Given that Agent represents a generic type it is RECOMMENDED that only subclasses of Agent be employed to represent nodes in the learning graph.

#### Superclass
[Entity](#entity)

#### Properties
Agent inherits all properties defined by its superclass [Entity](#entity).  Additional requirements are described below:

* `type`: the string value `Agent` MUST be specified.

#### Subclasses 
[Organization](#organization), [Person](#person), [SoftwareApplication](#softwareapplication)

#### Example
```json
{
    TODO
}
```

<a name="annotation" />

### 7.2 Annotation
A Caliper Annotation is a generic class that represents a comment, explanation, highlight, mark, note, question or tag linked to a [DigitalResource](#digitalResource).  The act of sharing a [DigitalResource](#digitalResource) with others is also considered a form of annotation.  Given that Annotation represents a generic type it is RECOMMENDED that only subclasses of Annotation be employed to represent nodes in the learning graph.

#### Superclass
[Entity](#entity)

#### Properties
Annotation inherits all properties defined by its superclass [Entity](#entity).  Additional properties and requirements are described below:

* `type`: the string value `Annotation` MUST be specified.
* `annotator`: the [Agent](#agent), typically a [Person](#person) who created the Annotation SHOULD be specified.
* `annotated`: the [DigitalResource](#digitalResource) that was annotated by the actor SHOULD be specified.  Note that DigitalResource is a generic type that is subtyped for more precise type specificity.  Utilize DigitalResource only if no suitable subtype exists to represent the annotated resource.

#### Subclasses 
[BookmarkAnnotation](#bookmarkAnnotation), [HighlightAnnotation](#highlightAnnotation), [SharedAnnotation](#sharedAnnotation), [TagAnnotation](#tagAnnotation)

#### Example
```json
{
    TODO
}
```

<a name="assessment" />

### 7.3 Assessment
A Caliper Assessment represents an assessment instrument such as a test or quiz.

#### Superclass
[DigitalResourceCollection](#digitalResourceCollection), [AssignableDigitalResource](#assignableDigitalResource)

#### Properties
Assessment inherits all the properties and requirements defined by its superclasses [DigitalResourceCollection](#digitalResourceCollection) and [AssignableDigitalResource](#assignableDigitalResource).  Additional requirements are described below:

* `type`: the string value `Assessment` MUST be specified.
* `items`: an optional ordered collection of [AssessmentItem](#assessmentItem) entities contained in the Assessment MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
  "type": "Assessment",
  "name": "Quiz One",
  "items": [
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1",
      "type": "AssessmentItem"
    },
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2",
      "type": "AssessmentItem"
    },
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "type": "AssessmentItem"
    }
  ],
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z",
  "datePublished": "2016-08-15T09:30:00.000Z",
  "dateToActivate": "2016-08-16T05:00:00.000Z",
  "dateToShow": "2016-08-16T05:00:00.000Z",
  "dateToStartOn": "2016-08-16T05:00:00.000Z",
  "dateToSubmit": "2016-09-28T11:59:59.000Z",
  "maxAttempts": 2,
  "maxScore": 15,
  "maxSubmits": 2,
  "version": "1.0"
}
```
<a name="assessmentItem" />

### 7.4 AssessmentItem
A Caliper AssessmentItem represents a single test question.

#### Superclass
[AssignableDigitalResource](#assignableDigitalResource)

#### Properties
AssessmentItem inherits all the properties and requirements defined by its superclass [AssignableDigitalResource](#assignableDigitalResource).  Additional requirements are described below:

* `type`: the string value `AssessmentItem` MUST be specified.
* `isTimeDependent`: an optional boolean value indicating whether or not interacting with the item is time dependent MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
  "type": "AssessmentItem",
  "isPartOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "type": "Assessment"
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "datePublished": "2016-08-15T09:30:00.000Z",
  "isTimeDependent": false,
  "maxAttempts": 2,
  "maxScore": 5,
  "maxSubmits": 2,
  "extensions": {
    "@context": {
      "@vocab": "http://example.edu/ctx/edu.jsonld"
    },
    "itemType": "true/false",
    "itemText": "In Caliper event actors are limited to people only.",
    "itemCorrectResponse": false
  }
}
```

<a name="assignableDigitalResource" />

### 7.5 AssignableDigitalResource
A Caliper AssignableDigitalResource is a generic class that represents digital content associated with a graded or ungraded assignment.  Given that AssignableDigitalResource represents a generic type it is RECOMMENDED that only subclasses of AssignableDigitalResource be employed to represent nodes in the learning graph.

#### Superclass
[DigitalResource](#digitalResource)

#### Properties
AssignableDigitalResource inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional properties and requirements are described below:

* `type`: the string value `AssignableDigitalResource` MUST be specified.
* `dateToActivate`: an optional date and time value expressed with millisecond precision that describes when the assigned resource was activated MAY be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string.
* `dateToShow`: an optional date and time value expressed with millisecond precision that describes when the assigned resource should be shown or made available to learners MAY be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.
* `dateToStartOn`: an optional date and time value expressed with millisecond precision that describes when the assigned resource can be started MAY be specified..  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.
* `maxAttempts`: an optional non-negative integer representing the number of permitted attempts MAY be specified.
* `maxSubmits`: an optional non-negative integer representing the number of permitted submissions MAY be specified.
* `maxScore`: an optional non-negative integer representing the maximum score permitted MAY be specified.

#### Subclasses 
[Assessment](#assessment), [AssessmentItem](#assessmentItem)

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assign/2",
  "type": "AssignableDigitalResource",
  "name": "Week 9 Reflection",
  "description": "3-5 page reflection on this week's assigned readings.",
  "dateCreated": "2016-11-01T06:00:00.000Z",
  "dateToActivate": "2016-11-10T11:59:59.000Z",
  "dateToShow": "2016-11-10T11:59:59.000Z",
  "dateToStartOn": "2016-11-10T11:59:59.000Z",
  "dateToSubmit": "2016-11-14T11:59:59.000Z",
  "maxAttempts": 2,
  "maxSubmits": 2,
  "maxScore": 50
}
```

<a name="attempt" />

### 7.6 Attempt
A Caliper Attempt provides a count of the number of times an actor has interacted with an [AssignableDigitalResource](#assignabledigitalresource) along with start time, end time and duration information.  An Attempt is generated as the result of an action such as starting an [Assessment](#assessment).

#### Superclass
[Entity](#entity)

#### Properties
Attempt inherits all the properties and requirements defined for its superclass [Entity](#entity).  Additional properties and requirements are described below:

* `type`: the string value `Attempt` MUST be specified.
* ~~`actor`: the [Person](#person) who initiated the Attempt SHOULD be specified.~~ Deprecated in favor of `assignee`.
* `assignee`: the [Agent](#agent), typically a [Person](#person) who initiated the Attempt SHOULD be specified.
* `assignable`: the [DigitalResource](#digitalResource) that constitutes the object of the assignment SHOULD be specified.  Note that DigitalResource is a generic type that is subtyped for more precise type specificity.  Utilize DigitalResource only if no suitable subtype exists to represent the annotated resource.
* `isPartOf`: the parent Attempt of this Attempt MAY be specified.
* `count`: the total number of attempts inclusive of the current Attempt that have been registered against the assigned [DigitalResource](#digitalResource) SHOULD be specified.
* `startedAtTime`: an optional date and time value expressed with millisecond precision that describes when this Attempt was commenced SHOULD be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime).
* `endedAtTime`: an optional date and time value expressed with millisecond precision that describes when this Attempt was terminated.  For a [completed](#completed) or [submitted](#submitted) action an end time SHOULD be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime).
* `duration`: an optional time interval that represents the time taken to complete this Attempt MAY be specified.  If a duration is specified the value MUST conform to the ISO-8601 duration format.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
  "type": "Attempt",
  "assignable": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "type": "Assessment"
  },
  "assignee": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "count": 1,
  "dateCreated": "2016-11-15T10:05:00.000Z",
  "startedAtTime": "2016-11-15T10:05:00.000Z",
  "endedAtTime": "2016-11-15T10:55:30.000Z",
  "duration": "PT50M30S"
}
```

<a name="audioObject" />

### 7.7 AudioObject
A Caliper AudioObject represents an audio or sound file.  It is analogous to a [schema:AudioObject](http://schema.org/AudioObject).

#### Superclass
[MediaObject](#mediaObject)

#### Properties
AudioObject inherits all the properties and requirements defined for its superclass [MediaObject](#mediaObject).  Additional properties are described below:

* `type`: the string value `AudioObject` MUST be specified.
* `volumeMin`: an optional string value indicating the minimum volume level MAY be specified.
* `volumeMax`: an optional string value indicating the maximum volume level MAY be specified.
* `volumeLevel`: an optional string value indicating the current volume level MAY be specified.
* `muted`: an optional boolean value indicating whether or not the AudioObject has been muted MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/audio/765",
  "type": "AudioObject",
  "name": "Audio Recording: IMS Caliper Sensor API Q&A.",
  "mediaType": "audio/ogg",
  "datePublished": "2016-12-01T06:00:00.000Z",
  "duration": "PT55M13S"
}
```

<a name="bookmarkAnnotation" />

### 7.8 BookmarkAnnotation
A Caliper BookmarkAnnotation represents the act of marking a [DigitalResource](#digitalResource) at a particular location.

#### Superclass
[Annotation](#annotation)

#### Properties
BookmarkAnnotation inherits all the properties and requirements defined for its superclass [Annotation](#annotation).  Additional properties and requirements are described below:

* `type`: the string value `BookmarkAnnotation` MUST be specified.
* `bookmarkNotes`: an optional string value comprising a plain-text rendering of the note that accompanies the bookmark MAY be specified.    

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/users/554433/etexts/201/bookmarks/1",
  "type": "BookmarkAnnotation",
  "assignee": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "annotated": {
    "id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!/4[body01]/10[para05]/1:20)",
    "type": "Chapter"
  },
  "bookmarkNotes": "Caliper profiles model discrete learning activities or supporting activities that facilitate learning.",
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="chapter" />

### 7.9 Chapter
A Caliper Chapter represents a major sub-division of a piece of digital content.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
Chapter inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below:

* `type`: the string value `Chapter` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!)",
  "type": "Chapter",
  "name": "The Caliper Information Model",
  "isPartOf": {
    "id": "https://example.edu/etexts/201.epub",
    "type": "Document",
    "dateCreated": "2016-10-01T06:00:00.000Z",
    "name": "IMS Caliper Implementation Guide",
    "version": "1.1"
  }
}
```

<a name="courseOffering" />

### 7.10 CourseOffering
A Caliper CourseOffering represents the occurrence of a course or a class during a specified time period.  CourseOffering is composed of a subset of properties specified in the IMS [LTI 2.0](#lti) specification, which in turn, draws inspiration from the IMS [LIS 1.0](#lis) specification.

#### Superclass
[Organization](#organization)

#### Properties
CourseOffering inherits all the properties and requirements defined for its superclass [Organization](#organization).  Additional properties and requirements are described below:

* `type`: the string value `CourseOffering` MUST be specified. 
* `courseNumber`: an optional string value that constitutes a human-readable identifier for this CourseOffering SHOULD be specified.
* `academicSession`: an optional string value that constitutes a human-readable identifier for the designated period in which this CourseOffering occurs MAY be specified.

#### Subclasses 
[CourseSection](#courseSection)

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7",
  "type": "CourseOffering",
  "courseNumber": "CPS 435",
  "academicSession": "Fall 2016",
  "name": "CPS 435 Learning Analytics",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="courseSection" />

### 7.11 CourseSection
A Caliper CourseSection represents a specific instance of a [CourseOffering](#courseOffering) occuring during a specific semester, term or period.  CourseSection is composed of a subset of properties specified in the IMS [LTI 2.0](#lti) specification, which in turn, draws inspiration from the IMS [LIS 1.0](#lis) specification.

#### Superclass
[CourseOffering](#courseOffering)

#### Properties
CourseSection inherits all the properties and requirements defined for its superclass [CourseOffering](#courseOffering).  Additional properties and requirements are described below:

* `type`: the string value `CourseSection` MUST be specified. 
* `category`: an optional string value that characterizes the purpose of the section such as "lecture", "lab" or "seminar" MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1",
  "type": "CourseSection",
  "academicSession": "Fall 2016",
  "courseNumber": "CPS 435-01",
  "name": "CPS 435 Learning Analytics, Section 01",
  "category": "seminar",
  "subOrganizationOf": {
    "id": "https://example.edu/terms/201601/courses/7",
    "type": "CourseOffering",
    "courseNumber": "CPS 435"
  },
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="digitalResource" />

### 7.12 DigitalResource
A Caliper DigitalResource is a generic class that represents a content item.  Given that DigitalResource represents a generic type it is RECOMMENDED that only subclasses of DigitalResource be employed to represent nodes in the learning graph.  DigitalResource is analogous to a [schema:CreativeWork](https://schema.org/CreativeWork).

#### Superclass 
[Entity](#entity)

#### Properties
DigitalResource inherits all the properties and requirements defined for its superclass [Entity](#entity).  Additional properties and requirements are described below:

* `type`: the string value `DigitalResource` MUST be specified. 
* `creators`: an optional ordered list of [Agent](#agent) entities typically of type [Person](#person), that are responsible for bringing this DigitalResource into being MAY be specified.
* `mediaType`: an optional string value drawn from the list of [IANA](https://www.iana.org/assignments/media-types/media-types.xhtml) approved media types and subtypes that identifies the file format of this DigitalResource MAY be specified.
* ~~`objectType`: an optional string value that designates the type of this DigitalResource.~~ DEPRECATED and SHOULD NOT be referenced.
* `keywords`: an optional ordered collection of one or more string values that represent tags or labels that are used to identify this DigitalResource MAY be specified.  Analogous to [schema:keywords](http://schema.org/keywords).
* `learningObjectives`: an optional ordered collection of one or more [LearningObjectives](#learningobjective) entities that describe what a learner is expected to comprehend or accomplish after engaging with this DigitalResource MAY be specified.
* ~~`alignedlearningObjective`: an optional ordered collection of one or more [LearningObjectives](#learningobjective) entities that describe what a learner is expected to comprehend or accomplish after engaging with this DigitalResource MAY be specified.~~  DEPRECATED in favor of `learningObjectives`.
* `isPartOf`: a related [Entity](#entity), typically a DigitalResource, that includes or incorporates this DigitalResource as a part of its whole MAY be specified.  Analogous to [schema:isPartOf](http://schema.org/isPartOf) or [dcterms:isPartOf](http://purl.org/dc/terms/isPartOf).
* `datePublished`: an optional date and time value expressed with millisecond precision that provides the publication date of this DigitalResource.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.  Analogous to [schema:datePublished](http://schema.org/datePublished).
* `version`: an optional string value that designates the current form or version of this DigitalResource.  Analogous to [schema:version](http://schema.org/version).

#### Subclasses
[AssignableDigitalResource](#assignableDigitalResource), [Chapter](#chapter), [DigitalResourceCollection](#digitalResourceCollection), [Document](#document), [Forum](#forum), [Frame](#frame), [MediaLocation](#mediaLocation), [MediaObject](#mediaobject), [Message](#message), [Page](#page), [Thread](#thread), [WebPage](#webpage)

#### Deprecated subclasses
[EpubChapter](#epubChapter), [EpubPart](#epubPart), [EpubSubChapter](#epubSubChapter), [EpubVolume](#epubVolume), [Reading](#reading)

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/1/syllabus.pdf",
  "type": "DigitalResource",
  "name": "Course Syllabus",
  "mediaType": "application/pdf",
  "creators": [
    {
      "id": "https://example.edu/users/223344",
      "type": "Person"
    }
  ],
  "isPartOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/1",
    "type": "DigitalResourceCollection",
    "name": "Course Assets",
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection"
    }
  },
  "dateCreated": "2016-08-02T11:32:00.000Z"
}
```

<a name="digitalResourceCollection" />

### 7.13 DigitalResourceCollection
A Caliper DigitalResourceCollection represents an ordered collection of [DigitalResource](#digitalResources) entities.

#### Superclass
[DigitalResource](#digitalResource)

#### Properties
DigitalResourceCollection inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResources).  Additional properties and requirements are described below:

* `type`: the string value `DigitalResourceCollection` MUST be specified. 
* `items`: an optional ordered collection of [DigitalResource](#digitalResources) entities that comprise this collection MAY be specified.

#### Subclasses 
[Assessment](#assessment), [Forum](#forum), [Thread](#thread)

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/resources/2",
  "type": "DigitalResourceCollection",
  "name": "Video Collection",
  "keywords": ["collection", "videos"],
  "items": [
    {
      "id": "https://example.edu/videos/1225",
      "type": "VideoObject",
      "mediaType": "video/ogg",
      "name": "Introduction to IMS Caliper",
      "dateCreated": "2016-08-01T06:00:00.000Z",
      "duration": "PT1H12M27S",
      "version": "1.1"
    },
    {
      "id": "https://example.edu/videos/5629",
      "type": "VideoObject",
      "mediaType": "video/ogg",
      "name": "IMS Caliper Activity Profiles",
      "dateCreated": "2016-08-01T06:00:00.000Z",
      "duration": "PT55M13S",
      "version": "1.1.1"
    }
  ],
  "isPartOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "subOrganizationOf": {
      "id": "https://example.edu/terms/201601/courses/7",
      "type": "CourseOffering"
    }
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="document" />

### 7.14 Document
A Caliper Document represents a piece of digital content.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
Document inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional properties and requirements are described below:

* `type`: the string value `Document` MUST be specified. 

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/etexts/201.epub",
  "type": "Document",
  "name": "IMS Caliper Implementation Guide",
  "mediaType": "application/epub+zip",
  "creators": [
    {
      "id": "https://example.edu/people/12345",
      "type": "Person"
    },
    {
      "id": "https://example.com/staff/56789",
      "type": "Person"
    }
  ],
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "datePublished": "2016-10-01T06:00:00.000Z",
  "version": "1.1"
}
```
 
<a name="epubChapter" />

### 7.15 EpubChapter (DEPRECATED)
A Caliper EpubChapter represents a major structural division of a piece of writing.  EpubChapter is a DEPRECATED entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
EpubChapter inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below:

* `type`: the string value `EpubChapter`.

<a name="epubPart" />

### 7.16 EpubPart (DEPRECATED)
A Caliper EpubPart represents a major structural division of a piece of writing, typically encapsulating a set of related chapters.  EpubPart is a DEPRECATED entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
EpubPart inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below:

* `type`: the string value `EpubPart`. 

<a name="epubSubChapter" />

### 7.17 EpubSubChapter (DEPRECATED)
A Caliper EpubSubChapter represents a major sub-division of an [EpubChapter](#EpubChapter).  EpubSubChapter is a DEPRECATED entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
EpubSubChapter inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below:

* `type`: the string value `EpubSubChapter`.

<a name="epubVolume" />

### 7.18 EpubVolume (DEPRECATED)
A Caliper EpubVolume represents a component of a collection.  EpubVolume inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  EpubVolume is a DEPRECATED entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
EpubVolume inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below: 

* `type`: the string value `EpubVolume`.

<a name="fillinBlankResponse" />

### 7.19 FillinBlankResponse
A Caliper FillinBlankResponse represents a form of response in which a respondent is asked to provide one or more words, expressions or short phrases that correctly completes a statement.

#### Superclass 
[Response](#response)

#### Properties
FillinBlankResponse inherits all the properties and requirements defined for its superclass [Response](#response).  Additional properties and requirements are described below: 

* `type`: the string value `FillinBlankResponse` MUST be specified.
* `values`: an optional ordered collection of one or more string values representing words, expressions or short phrases that constitutes the FillinBlankResponse MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1/users/554433/responses/1",
  "type": "FillinBlankResponse",
  "attempt": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1",
      "type": "AssessmentItem",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment"
      }
    },
    "count": 1,
    "startedAtTime": "2016-11-15T10:15:02.000Z",
    "endedAtTime": "2016-11-15T10:15:12.000Z"
  },
  "dateCreated": "2016-11-15T10:15:12.000Z",
  "startedAtTime": "2016-11-15T10:15:02.000Z",
  "endedAtTime": "2016-11-15T10:15:12.000Z",
  "values": [ "data interoperability", "semantic interoperability" ]
}
```

<a name="forum" />

### 7.20 Forum
A Caliper Forum represents a channel or virtual space in which group discussions take place.  A Forum typically comprises one or more threaded conversations to which members can subscribe, post messages and reply to other messages.  It is analogous to a [sioc:Forum](http://rfds.org/sioc/spec/#term_Forum).

#### Superclass 
[DigitalResourceCollection](#digitalResourceCollection)

#### Properties
Frame inherits all the properties and requirements defined for its superclass [DigitalResourceCollection](#digitalResourceCollection).  Additional properties and requirements are described below: 
  
 * `type`: the string value `Forum` MUST be specified. 
 * `items`: an optional ordered collection of [Thread](#thread) entities that comprise this Forum MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
  "type": "Forum",
  "name": "Caliper Forum",
  "items": [
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1",
      "type": "Thread",
      "name": "Caliper Information Model",
      "dateCreated": "2016-11-01T09:30:00.000Z"
    },
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/2",
      "type": "Thread",
      "name": "Caliper Sensor API",
      "dateCreated": "2016-11-01T09:30:00.000Z"
    },
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/3",
      "type": "Thread",
      "name": "Caliper Certification",
      "dateCreated": "2016-11-01T09:30:00.000Z"
    }
  ],
  "isPartOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "subOrganizationOf": {
      "id": "https://example.edu/terms/201601/courses/7",
      "type": "CourseOffering"
    }
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="frame" />

### 7.21 Frame
A Caliper Frame represents a part, portion or segment of a [DigitalResource](#digitalResource).
 
#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
Frame inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional properties and requirements are described below: 

* `type`: the string value `Frame` MUST be specified.
* `index`: an optional non-negative integer that representes the character position TODO . . . . SHOULD be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/etexts/201?index=2502",
  "type": "Frame",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "index": 2502,
  "isPartOf": {
    "id": "https://example.edu/etexts/201",
    "type": "Document",
    "name": "IMS Caliper Implementation Guide",
    "version": "1.1"
  }
} 
```

<a name="group" />

### 7.22 Group
A Caliper Group represents a ad-hoc, informal or short-lived collection of people organized for some common educational or social purpose.  The Group can act as an [Agent](#agent) and can be decomposed into sub-groups.

#### Superclass
[Organization](#organization)

#### Properties
Group inherits all the properties and requirements defined for its superclass [Organization](#organization).  Additional requirements are described below: 

* `type`: the string value `Group` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/groups/2",
  "type": "Group",
  "name": "Discussion Group 2",
  "subOrganizationOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "subOrganizationOf": {
      "id": "https://example.edu/terms/201601/courses/7",
      "type": "CourseOffering"
    }
  },
  "dateCreated": "2016-11-01T06:00:00.000Z"
}
```

<a name="highlightAnnotation" />

### 7.23 HighlightAnnotation
A Caliper HighlightAnnotation represents the act of marking a particular segment of a [DigitalResource](#digitalResource) between two known coordinates.  

### TODO
* Add additional instructions regarding start and end properties

#### Superclass
[Annotation](#annotation)

#### Properties
HighlightAnnotation inherits all the properties and requirements defined for its superclass [Annotation](#annotation).  Additional properties and requirements are described below: 

* `type`: the string value `HighlightAnnotation` MUST be specified.
* `selection`: an optional [TextPositionSelector](#textPositionSelector) MAY be specified.  If a TextPositionSelector is defined both its [start](#start) and [end](#end) positions MUST be specified.
* `selectionText`: an optional string value representing a plain-text rendering of the highlighted segment of the annotated DigitalResource MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/users/554433/etexts/201/highlights/20",
  "type": "HighlightAnnotation",
  "assignee": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "annotated": {
    "id": "https://example.edu/etexts/201",
    "type": "Document"
  },
  "selection": {
    "type": "TextPositionSelector",
    "start": 2300,
    "end": 2370
  },
  "selectionText": "ISO 8601 formatted date and time expressed with millisecond precision.",
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="imageObject" />

### 7.24 ImageObject
A Caliper ImageObject represents an image file.  It is analogous to [schema:ImageObject](http://schema.org/ImageObject).

#### Superclass 
[MediaObject](#mediaObject)

#### Properties
ImageObject inherits all the properties and requirements defined for its superclass [MediaObject](#mediaObject).  Additional requirements are described below:

* `type`: the string value `ImageObject` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/images/caliper_lti.jpg",
  "type": "ImageObject",
  "name": "IMS Caliper/LTI Integration Work Flow",
  "mediaType": "image/jpeg",
  "dateCreated": "2016-09-01T06:00:00.000Z"
}
```

<a name="learningObjective" />

### 7.25 LearningObjective
The Caliper LearningObjective represents a summary statement that outlines the learning-related goals that a learner is expected to attain as a result of engaging in a learning activity.

#### Superclass 
[Entity](#entity)

#### Properties
LearningObjective inherits all the properties and requirements defined for its superclass [Entity](#entity).  Additional requirements are described below:

* `type`: the string value `LearningObjective` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assign/2",
  "type": "AssignableDigitalResource",
  "name": "Caliper Profile Design",
  "description": "Choose a learning activity and describe the actions, entities and events that comprise it.",
  "learningObjectives": [
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/objectives/1",
      "type": "LearningObjective",
      "name": "Research techniques",
      "description": "Demonstrate ability to model a learning activity as a Caliper profile.",
      "dateCreated": "2016-08-01T06:00:00.000Z"
    }
  ],
  "dateToActivate": "2016-11-10T11:59:59.000Z",
  "dateToShow": "2016-11-10T11:59:59.000Z",
  "dateCreated": "2016-11-01T06:00:00.000Z",
  "dateToStartOn": "2016-11-15T11:59:59.000Z",
  "dateToSubmit": "2016-11-14T11:59:59.000Z",
  "maxAttempts": 2,
  "maxSubmits": 2,
  "maxScore": 50
}
```

<a name="ltiSession" />

### 7.26 LtiSession
A Caliper LtiSession represents an LTI Tool Consumer user session.

#### Superclass
[Session](#session)

#### Properties
LtiSession inherits all the properties and requirements defined for its superclass [Session](#session).  Additional properties and requirements are described below:

* `type`: the string value `LtiSession` MUST be specified.
* `launchParameters`: an optional object comprising LTI-specified launch parameters that provide Tool Consumer-related contextual information MAY be specfied.  LTI parameters of whatever type (i.e., required, recommended, optional, custom and extension) included in the launch request message MAY be referenced.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.com/sessions/b533eb02823f31024e6b7f53436c42fb99b31241",
  "type": "LtiSession",
  "user": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "launchParameters": {
    "lti_message_type": "basic-lti-launch-request",
    "lti_version": "LTI-2p0",
    "resource_link_id": "88391-e1919-bb3456",
    "context_id": "8213060-006f-27b2066ac545",
    "launch_presentation_document_target": "iframe",
    "launch_presentation_height": 240,
    "launch_presentation_return_url": "https://example.edu/terms/201601/courses/7/sections/1/pages/5",
    "launch_presentation_width": 320,
    "roles": "Learner,Student",
    "tool_consumer_instance_guid": "example.edu",
    "user_id": "0ae836b9-7fc9-4060-006f-27b2066ac545",
    "context_type": "CourseSection",
    "launch_presentation_locale": "en-US",
    "launch_presentation_css_url": "https://example.edu/css/tool.css",
    "role_scope_mentor": "f5b2cc6c-8c5c-24e8-75cc-fac5,dc19e42c-b0fe-68b8-167e-4b1a",
    "custom_caliper_session_id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "custom_context_title": "CPS 435 Learning Analytics",
    "custom_context_label": "CPS 435",
    "custom_resource_link_title": "LTI tool",
    "custom_user_image": "https://example.edu/users/554433/profile/avatar.jpg",
    "ext_vnd_instructor": {
      "@context": {
        "@vocab": "http://example.edu/ctx/edu.jsonld",
        "sdo": "http://schema.org/"
      },
      "type": "Faculty",
      "schema:jobTitle": "Professor",
      "schema:givenName": "Trig",
      "schema:familyName": "Haversine",
      "schema:email": "trighaversine@example.edu",
      "schema:url": "https://example.edu/faculty/trighaversine",
      "isTenured": true,
      "isOnSabbatical": false
    }
  },
  "dateCreated": "2016-11-15T10:15:00.000Z",
  "startedAtTime": "2016-11-15T10:15:00.000Z"
}
```

<a name="mediaLocation" />

### 7.27 MediaLocation

A Caliper MediaLocation provides the current playback position in an [AudioObject](#audioObject) or [VideoObject](#videoObject).
 
#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
MediaLocation inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional properties and requirements are described below: 

* `type`: the string value `MediaLocation` MUST be specified.
* `currentTime`: an optional time interval that represents the current playback position measured from the beginning of an [AudioObject](#audioObject) or [VideoObject](#videoObject) MAY be specified.  If a currentTime is specified the value MUST conform to the ISO-8601 duration format.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/videos/1225",
  "type": "MediaLocation",
  "currentTime": "PT30M54S",
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="mediaObject" />

### 7.28 MediaObject
A Caliper MediaObject represents a generic piece of media content.  Given that MediaObject represents a generic type it is RECOMMENDED that only subclasses of MediaObject be employed to represent nodes in the learning graph.  MediaObject is analogous to [schema:MediaObject](http://schema.org/MediaObject).

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
MediaObject inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional properties and requirements are described below: 

* `type`: the string value `MediaObject` MUST be specified.
* `duration`: an optional time interval that represents the total time required to view and/or listen to this MediaObject at normal speed MAY be specified.  If a duration is specified the value MUST conform to the ISO-8601 duration format.

#### Subclasses
[AudioObject](#audioObject.md), [ImageObject](#imageObject.md), [VideoObject](#videoObject)

#### Example
```json
{
  TODO
}
```

<a name="membership" />

### 7.29 Membership
A Caliper Membership describes the relationship between an [Organization](#organization) and a [Person](#person) (i.e., a [member](#member)) in terms of the roles assigned and current status.  

#### Superclass 
[Entity](#entity)

#### Properties
Membership inherits all the properties and requirements defined for its superclass [Entity](#entity).  Additional properties and requirements are described below: 

* `type`: the string value `Membership` MUST be specified.
* `organization`: the [Organization](#organization) associated with this Membership SHOULD be specified.
* `member`: the [Person](#person) associated with this Membership SHOULD be specified.
* `roles`: an optional ordered collection of organizational roles assigned to the member SHOULD be specified.  If one or more rols are specified the value(s) MUST be chosen from the list of Caliper defined [roles](#roles].
* `status`: an optional string value that indicates the member's current status SHOULD be specified.  If a status is specified, the value MUST be set to the one of the following defined states:  [Active](#active) or [Inactive](#inactive).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1/members/554433",
  "type": "Membership",
  "member": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "organization": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "subOrganizationOf": {
      "id": "https://example.edu/terms/201601/courses/7",
      "type": "CourseOffering"
    }
  },
  "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
  "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
  "dateCreated": "2016-11-01T06:00:00.000Z"
}
```

<a name="message" />

### 7.30 Message
A Caliper Message is a digital form of written communication sent to a recipient. A series of messages may constitute a [Thread](#thread) if they share a common subject and are connected by a reply or by date relationships.  It is analogous to an [sioc:Post](http://rfds.org/sioc/spec/#term_Post).

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
Message inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional properties and requirements are described below: 

* `type`: the string value `Message` MUST be specified.
* `replyTo`: a [Message](#message) that represents the post to which this Message is directed in reply SHOULD be referenced.  Analogous to [sioc:reply_of](http://rdfs.org/sioc/spec/#term_reply_of).
* `body`: an optional string value comprising a plain-text rendering of the body content of the Message MAY be specified.  Analogous to [sioc:content](http://rdfs.org/sioc/spec/#content). |
* `attachments`: | an optional ordered collection of one or more [DigitalResource](#digitalResource) entities attached to this Message MAY be specified.  Analogous to [sioc:attachment](http://rdfs.org/sioc/spec/#term_attachment).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/3",
  "type": "Message",
  "creators": [
    {
      "id": "https://example.edu/users/778899",
      "type": "Person"
    }
  ],
  "body": "The Caliper working group provides a set of Caliper Sensor reference implementations for the purposes of education and experimentation.  They have not been tested for use in a production environment.  See the Caliper Implementation Guide for more details.",
  "replyTo": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/2",
    "type": "Message"
  },
  "isPartOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1",
    "type": "Thread",
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2",
      "type": "Forum"
    }
  },
  "attachments": [
    {
      "id": "https://example.edu/etexts/201.epub",
      "type": "Document",
      "name": "IMS Caliper Implementation Guide",
      "dateCreated": "2016-10-01T06:00:00.000Z",
      "version": "1.1"
    }
  ],
  "dateCreated": "2016-11-15T10:15:30.000Z"
}
 ```
 
<a name="multipleChoiceResponse" />

### 7.31 MultipleChoiceResponse
A Caliper MultipleChoiceResponse represents a form of response in which a respondent is asked to provide the best possible answer from a list of choices.

#### Superclass 
[Response](#response)

#### Properties
MultipleChoiceResponse inherits all the properties and requirements defined for its superclass [Response](#response).  Additional properties and requirements are described below:

* `type`: the string value `MultipleChoiceResponse` MUST be specified.
* `value`: an optional string value that represents the selected option SHOULD be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2/users/554433/responses/1",
  "type": "MultipleChoiceResponse",
  "attempt": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2",
      "type": "AssessmentItem",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment"
      }
    },
    "count": 1,
    "startedAtTime": "2016-11-15T10:15:14.000Z",
    "endedAtTime": "2016-11-15T10:15:20.000Z"
  },
  "dateCreated": "2016-11-15T10:15:20.000Z",
  "startedAtTime": "2016-11-15T10:15:14.000Z",
  "endedAtTime": "2016-11-15T10:15:20.000Z",
  "value": "C"
}
```

<a name="multipleResponseResponse" />

### 7.32 MultipleResponseResponse
A Caliper MultipleResponseResponse represents a form of response in which a respondent is asked to select more than one correct answer from a list of choices.

#### Superclass 
[Response](#response)

#### Properties
MultipleResponseResponse inherits all the properties and requirements defined for its superclass [Response](#response).  Additional properties and requirements are described below:

* `type`: the string value `MultipleResponseResponse` MUST be specified.
* `values`: an optional ordered collection of one or more selected options MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/responses/1",
  "type": "MultipleResponseResponse",
  "attempt": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "type": "AssessmentItem",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment"
      }
    },
    "count": 1,
    "startedAtTime": "2016-11-15T10:15:22.000Z",
    "endedAtTime": "2016-11-15T10:15:30.000Z"
  },
  "dateCreated": "2016-11-15T10:15:22.000Z",
  "startedAtTime": "2016-11-15T10:15:22.000Z",
  "endedAtTime": "2016-11-15T10:15:30.000Z",
  "values": [ "A", "D", "E" ]
}
```

<a name="organization" />

### 7.33 Organization
A Caliper Organization represents a formal collection of people organized for some common educational, social or administrative purpose.  The Organization can act as an [Agent] and can be decomposed into sub-organizations.  It is analogous to a [w3c:Organization](https://www.w3.org/TR/vocab-org/#class-organization).

#### Superclass
[Agent](#agent)

### Required properties
Organization inherits all the properties and requirements defined for [Agent](#agent), its superclass.  Additional properties and requirements are described below:

* `type`: the string value `Organization` MUST be specified.
* `subOrganizationOf`: the parent [Organization](#organization) of this Organization MAY be specified.
* `members`: ordered collection of [Agent](#agent) members MAY be specified.

#### Subclasses 
[CourseOffering](#CourseOffering), [CourseSection](#CourseSection), [Group](#group)

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/colleges/1/depts/1",
  "type": "Organization",
  "name": "Computer Science Department",
  "subOrganizationOf": {
    "id": "https://example.edu/colleges/1",
    "type": "Organization",
    "name": "College of Engineering"
  }
}
```

<a name="page" />

### 7.34 Page
A Caliper Page represents an item of paginated content.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
Page inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below:

* `type`: the string value `Page` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/etexts/201/chs/2/pp/23",
  "type": "Page",
  "name": "Page 23",
  "isPartOf": {
    "id": "https://example.edu/etexts/201/chs/2",
    "type": "Chapter",
    "name": "Chapter 2",
    "isPartOf": {
      "id": "https://example.edu/etexts/201",
      "type": "Document",
      "name": "IMS Caliper Implementation Guide",
      "dateCreated": "2016-10-01T06:00:00.000Z",
      "version": "1.1"
    }
  }
}
```

<a name="person" />

### 7.35 Person
A Caliper Person represents a human being, alive or deceased, real or imaginary.  It is analogous to a [foaf:Person](http://xmlns.com/foaf/spec/#term_Person).

#### Superclass
[Agent](#agent)

#### Properties
Person inherits all the properties and requirements defined for its superclass [Agent](#agent).  Additional requirements are described below:

* `type`: the string value `Person` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/users/554433",
  "type": "Person",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="reading" />

### 7.36 Reading (DEPRECATED)
A Caliper Reading represents an item of paginated content.  Reading is a DEPRECATED entity superceded by [Document](#document) that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
Reading inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below:

* `type`: the string value `Reading` MUST be specified.

<a name="response" />

### 7.37 Response
A Caliper Response is a generic class that represents the selected option generated by a [Person](#person) interacting with an [AssessmentItem](#assessmentItem).  Given that Response represents a generic type it is RECOMMENDED that only subclasses of Response be employed to represent nodes in the learning graph. 

#### Superclass 
[Entity](#entity)

#### Properties
Response inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional properties and requirements are described below:

* `type`: the string value `Response` MUST be specified.
* `attempt`: the associated [Attempt](#attempt) SHOULD be specified.  The Attempt SHOULD reference both the [Person](#person) who initiated the Response and the relevant [AssessmentItem](#assessmentItem).
* ~~`actor`: the [Person](#person) who initiated the Response.~~ DEPRECATED in favor of `attempt`.
* ~~`assignable`: the [DigitalResource](#digitalResource) that constitutes the `object` of the Response.~~ DEPRECATED in favor of `attempt`.
* `startedAtTime`: an optional date and time value expressed with millisecond precision that describes when this Response was commenced SHOULD be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime).
* `endedAtTime`: an optional date and time value expressed with millisecond precision that describes when this Response was submitted.  For a [completed](#completed) or [submitted](#submitted) action an end time SHOULD be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime).
* `duration`: an optional time interval that represents the time taken to complete this Response MAY be specified.  If a duration is specified the value MUST conform to the ISO-8601 duration format.

#### Subclasses
[FillinBlankResponse](#fillinblankResponse.md), [MultipleChoiceResponse](#multipleChoiceResponse), [MutlipleResponseResponse](#mutlipleResponseResponse), [SelectTextResponse](#selectTextResponse), [TrueFalseResponse](#trueFalseResponse)

<a name="result" />

### 7.38 Result
A Caliper Result represents a grade applied to an assignment submission.

#### Superclass 
[Entity](#entity)

#### Properties
Result inherits all the properties and requirements defined for its superclass [Entity](#entity).  Additional properties and requirements are described below:

* `type`: the string value `Result` MUST be specified.
* `attempt`: the associated [Attempt](#attempt) SHOULD be specified.  The Attempt SHOULD reference both the [Agent](#agent) who graded the Result and the relevant [DigitalResource](#digitalResource).
* `normalScore`: TODO
* `penaltyScore`: TODO
* `extraCreditScore`: TODO
* `totalScore`: TODO
* `curvedTotalScore`:  TODO
* `curveFactor`: TODO
* `comment`: TODO
* `scoredBy`: TODO

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1/results/1",
  "type": "Result",
  "attempt": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "type": "Assessment"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:05:00.000Z",
    "startedAtTime": "2016-11-15T10:05:00.000Z",
    "endedAtTime": "2016-11-15T10:55:30.000Z",
    "duration": "PT50M30S"
  },
  "comment": "Well done.",
  "normalScore": 15.0,
  "penaltyScore": 0.0,
  "totalScore": 15.0,
  "scoredBy": {
    "id": "https://example.edu/autograder",
    "type": "SoftwareApplication",
    "dateCreated": "2016-11-15T10:55:58.000Z"
  },
  "dateCreated": "2016-11-15T10:56:00.000Z"
}
```

<a name="selectTextResponse" />

### 7.39 SelectTextResponse
A Caliper SelectTextResponse represents a response that identifies text or a mapping from a presented paragraph or list.

#### Superclass 
[Response](#response)

#### Properties
SelectTextResponse inherits all the properties and requirements defined for its superclass [Response](#response).  Additional properties and requirements are described below:

* `type`: the string value `SelectTextResponse` MUST be specified.
* `values`: an optional ordered collection of one or more selected options MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/4/users/554433/responses/1",
  "type": "SelectTextResponse",
  "attempt": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/4/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/4",
      "type": "AssessmentItem",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment"
      }
    },
    "count": 1,
    "startedAtTime": "2016-11-15T10:15:32.000Z",
    "endedAtTime": "2016-11-15T10:15:38.000Z"
  },
  "dateCreated": "2016-11-15T10:15:32.000Z",
  "startedAtTime": "2016-11-15T10:15:32.000Z",
  "endedAtTime": "2016-11-15T10:15:38.000Z",
  "values": [ "Information Model", "Sensor API", "Profiles" ]
}
```

<a name="session" />

### 7.40 Session
A Caliper Session represents a web application user session.

#### Superclass
[Entity](#entity)

#### Properties
Session inherits all the properties and requirements defined for [Entity](#entity), its superclass.  Additional properties and requirements are described below:

* `type`: the string value `Session` MUST be specified.
* ~~`actor`: the [Person](#person) who initiated the Session SHOULD be specified.~~  DEPRECATED in favor of `user`.
* `user`: the [Person](#person), who initiated the Session SHOULD be specified.
* `startedAtTime`: an optional date and time value expressed with millisecond precision that describes when this Session was commenced SHOULD be specified.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime).
* `endedAtTime`: an optional date and time value expressed with millisecond precision that describes when this Session was terminated.  For a [loggedOut](#loggedOut) or [timedOut](#timedOut) action an end time SHOULD be provided.  The value MUST be expressed as an ISO-8601 formatted date/time string set to UTC.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime).
* `duration`: an optional time interval that represents the Session duration MAY be specified.  If a duration is specified the value MUST conform to the ISO-8601 duration format.

#### subclasses
[LtiSession](#ltiSession)

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
  "type": "Session",
  "user": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "startedAtTime": "2016-09-15T10:00:00.000Z"
}
```

<a name="sharedAnnotation" />

### 7.41 SharedAnnotation
A Caliper SharedAnnotation represents the act of sharing a reference to a DigitalResource with other agents.

#### Superclass
[Annotation](#annotation)

#### Properties
SharedAnnotation inherits all the properties and requirements defined for its superclass [Annotation](#annotation).  Additional properties and requirements are described below:

* `type`: the string value `SharedAnnotation` MUST be specified.
* `withAgents`: an optional ordered collection of one or more [Agent](#agent) entities, typically of type [Person](#person), with whom the annotated DigitalResource has been shared.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/users/554433/etexts/201/shares/1",
  "type": "SharedAnnotation",
  "assignee": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "annotated": {
    "id": "https://example.edu/etexts/201.epub",
    "type": "Document"
  },
  "withAgents": [
    {
      "id": "https://example.edu/users/657585",
      "type": "Person"
    },
    {
      "id": "https://example.edu/users/667788",
      "type": "Person"
    }
  ],
  "dateCreated": "2016-08-01T09:00:00.000Z"
}
```

<a name="softwareApplication" />

#### 7.42 SoftwareApplication
A Caliper SoftwareApplication represents a computer program, application, module, platform or system.  It is analogous to a [schema:SoftwareApplication](http://schema.org/SoftwareApplication) or [dcmitype:Software](http://purl.org/dc/dcmitype/Software).

#### Superclass
[Agent](#agent)

#### Properties
SoftwareApplication inherits all the properties and requirements defined for its superclass [Agent](#agent).  Additional properties and requirements are described below:

* `type`: the string value `SoftwareApplication` MUST be specified.
* `version`: an optional string value that designates the current form or version of this SoftwareApplication.  Analogous to [schema:version](http://schema.org/version).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/autograder",
  "type": "SoftwareApplication",
  "name": "Auto Grader",
  "description": "Automates assignment scoring.",
  "version": "2.5.2"
}
```

<a name="tagAnnotation" />

### 7.43 TagAnnotation
A Caliper TagAnnotation represents the act of tagging a DigitalResource with tags or labels.

#### Superclass
[Annotation](#annotation)

#### Properties
TagAnnotation inherits all the properties and requirements defined for its superclass [Annotation](#annotation).  Additional properties and requirements are described below:

* `type`: the string value `TagAnnotation` MUST be specified.
* `tags`: an optional ordered collection of one or more string values that represent the tags associated with the annotated [DigitalResource](#digitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/users/554433/etexts/201/tags/3",
  "type": "TagAnnotation",
  "assignee": {
    "id": "https://example.edu/users/554433",
    "type": "Person"
  },
  "annotated": {
    "id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!/4[body01]/12[para06]/1:97)",
    "type": "Chapter"
  },
  "tags": [ "profile", "event", "entity" ],
  "dateCreated": "2016-08-01T09:00:00.000Z"
}
```

<a name="thread" />

### 7.44 Thread
A Caliper Thread represents a series of one or more messages that share a common subject and are connected by a reply or by date relationships.

#### Superclass 
[DigitalResourceCollection](#digitalResourceCollection)

#### Properties
Thread inherits all the properties and requirements defined for its superclass [DigitalResourceCollection](#digitalResourceCollection).  Additional properties and requirements are described below:

* `type`: the string value `Thread` MUST be specified.
* `items`: an optional ordered collection of [Message](#message) entities that comprise this Forum MAY be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1",
  "type": "Thread",
  "name": "Caliper Information Model",
  "items": [
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/1",
      "type": "Message"
    },
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/2",
      "type": "Message",
      "replyTo": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/1",
        "type": "Message"
      }
    },
    {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/3",
      "type": "Message",
      "replyTo": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/2",
        "type": "Message"
      }
    }
  ],
  "isPartOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
    "type": "Forum",
    "name": "Caliper Forum",
    "isPartOf": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1",
      "type": "CourseSection",
      "subOrganizationOf": {
        "id": "https://example.edu/terms/201601/courses/7",
        "type": "CourseOffering"
      }
    }
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="trueFalseResponse" />

### 7.45 TrueFalseResponse
A Caliper TrueFalseResponse represents a response to a question in which only two possible options are provided (true/false, yes/no).

#### Superclass 
[Response](#response)

#### Properties
TrueFalseResponse inherits all the properties and requirements defined for [Response](#response), its superclass.  Additional properties and requirements are described below:

* `type`: the string value `TrueFalseResponse` MUST be specified.
* `value`: an optional string value that provides the true/false, yes/no binary selection SHOULD be provided.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/5/users/554433/responses/1",
  "type": "TrueFalseResponse",
  "attempt": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/5/users/554433/attempts/1",
    "type": "Attempt",
    "assignee": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "assignable": {
      "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/5",
      "type": "AssessmentItem",
      "isPartOf": {
        "id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "type": "Assessment"
      }
    },
    "count": 1,
    "startedAtTime": "2016-11-15T10:15:40.000Z",
    "endedAtTime": "2016-11-15T10:15:45.000Z"
  },
  "dateCreated": "2016-11-15T10:15:45.000Z",
  "startedAtTime": "2016-11-15T10:15:40.000Z",
  "endedAtTime": "2016-11-15T10:15:45.000Z",
  "value": "true"
}
```

<a name="videoObject" />

### 7.46 VideoObject
A Caliper VideoObject represents a visual recording stored in digital form.  It is analogous to [schema:VideoObject](http://schema.org/VideoObject).

#### Superclass 
[MediaObject](#mediaObject)

#### Properties
VideoObject inherits all the properties and requirements defined for its superclass [MediaObject](#mediaObject).  Additional requirements are described below:

* `type`: the string value `VideoObject` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/videos/1225",
  "type": "VideoObject",
  "mediaType": "video/ogg",
  "name": "Introduction to IMS Caliper",
  "version": "1.1",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z",
  "duration": "PT1H12M27S"
}
```

<a name="webPage" />

### 7.47 WebPage
A Caliper WebPage represents a document containing markup that is suitable for display in a web browser.  It is analogous to a [schema:WebPage](http://schema.org/WebPage).

#### Superclass 
[DigitalResource](#digitalResource)

#### Properties
WebPage inherits all the properties and requirements defined for its superclass [DigitalResource](#digitalResource).  Additional requirements are described below:

* `type`: the string value `WebPage` MUST be specified.

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1p1",
  "id": "https://example.edu/terms/201601/courses/7/sections/1/pages/index.html",
  "type": "WebPage",
  "name": "CPS 435-01 Landing Page",
  "mediaType": "text/html",
  "isPartOf": {
    "id": "https://example.edu/terms/201601/courses/7/sections/1",
    "type": "CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  }
}
```

<a name="#selectors" />

### 8.0 Appendix D. Selectors
TODO Intro

### 8.1 TextPositionSelector
TODO Intro

#### Properties

* `type`: the string value `TextPositionSelector` MUST be specified.
* `start`: TODO The start position . . . MUST be specified.
* `end`: TODO The end position . . . MUST be specified.

```json
{
    "id": "https://example.edu/users/554433/etexts/201/highlights?start=2300&end=2370",
    "type": "HighlightAnnotation",
    "annotator": {
      "id": "https://example.edu/users/554433",
      "type": "Person"
    },
    "annotated": {
      "id": "https://example.edu/etexts/201",
      "type": "Document"
    },
    "selection": {
      "type": "TextPositionSelector",
      "start": 2300,
      "end": 2370
    },
    "selectionText": "ISO 8601 formatted date and time expressed with millisecond precision.",
    "dateCreated": "2016-11-15T10:15:00.000Z"
}
```

<a name="roles" />

## 9.0 Appendix E. Roles

### Roles
One or more roles assigned to a [member](#member) of an organization can be specified.  Typical roles include learner, instructor, teaching assistant, mentor or administrator.  The value MUST be set to the appropriate term string value:

| Term | IRI |
| ----  | --- | 
| Learner | http://purl.imsglobal.org/vocab/lis/v2/membership#Learner |
| Learner#ExternalLearner | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#ExternalLearner |
| Learner#GuestLearner | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#GuestLearner |
| Learner#Instructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#Instructor |
| Learner#Learner | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#Learner |
| Learner#NonCreditLearner  | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#NonCreditLearner |

| Term | IRI |
| ----  | --- | 
| Instructor | http://purl.imsglobal.org/vocab/lis/v2/membership#Instructor |
| Instructor#ExternalInstructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#ExternalInstructor |
| Instructor#GuestInstructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#GuestInstructor |
| Instructor#Lecturer | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#Lecturer |
| Instructor#PrimaryInstructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#PrimaryInstructor |

| Term | IRI |
| ----  | --- | 
| Administrator | http://purl.imsglobal.org/vocab/lis/v2/membership#Administrator |
| Administrator#Administrator | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#Administrator |
| Administrator#Developer  | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#Developer |
| Administrator#Support | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#Support |
| Administrator#SystemAdministrator | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#SystemAdministrator |
| Administrator#ExternalSupport | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#ExternalSupport |
| Administrator#ExternalDeveloper | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#ExternalDeveloper |
| Administrator#ExternalSystemAdministrator | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#ExternalSystemAdministrator |

| Term | IRI |
| ----  | --- | 
| ContentDeveloper | http://purl.imsglobal.org/vocab/lis/v2/membership#ContentDeveloper |
| ContentDeveloper#ContentDeveloper | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#ContentDeveloper |
| ContentDeveloper#Librarian | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#Librarian |
| ContentDeveloper#ContentExpert | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#ContentExpert |
| ContentDeveloper#ExternalContentExpert | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#ExternalContentExpert |

| Tern | IRI |
| ----  | --- | 
| Manager | http://purl.imsglobal.org/vocab/lis/v2/membership#Manager |
| Manager#AreaManager | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#AreaManager |
| Manager#CourseCoordinator | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#CourseCoordinator |
| Manager#Observer | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#Observer",
| Manager#ExternalObserver | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#ExternalObserver |

| Term | IRI |
| ----  | --- | 
| Member | http://purl.imsglobal.org/vocab/lis/v2/membership#Member |
| Member#Member | http://purl.imsglobal.org/vocab/lis/v2/membership/Member#Member |

| Term | IRI |
| ----  | --- | 
| Mentor | http://purl.imsglobal.org/vocab/lis/v2/membership#Mentor |
| Mentor#Mentor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Mentor |
| Mentor#ExternalMentor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalMentor |
| Mentor#Advisor |  http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Advisor |
| Mentor#ExternalAdvisor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalAdvisor |
| Mentor#Auditor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Auditor |
| Mentor#ExternalAuditor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalAuditor |
| Mentor#LearningFacilitator | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#LearningFacilitator |
| Mentor#ExternalLearningFacilitator | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalLearningFacilitator |
| Mentor#Reviewer |  http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Reviewer |
| Mentor#ExternalReviewer | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalReviewer |
| Mentor#Tutor |  http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Tutor |
| Mentor#ExternalTutor | "http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalTutor |

| Term | IRI |
| ----  | --- | 
| TeachingAssistant | http://purl.imsglobal.org/vocab/lis/v2/membership#TeachingAssistant |
| TeachingAssistant#TeachingAssistant | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistant |
| TeachingAssistant#Grader | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#Grader |
| TeachingAssistant#TeachingAssistantSection | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantSection |
| TeachingAssistant#TeachingAssistantSectionAssociation | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantSectionAssociation |
| TeachingAssistant#TeachingAssistantOffering | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantOffering |
| TeachingAssistant#TeachingAssistantTemplate | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantTemplate |
| TeachingAssistant#TeachingAssistantGroup | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantGroup |

<a name="status" />

### 10.0 Appendix F. Status
The status of a [member](#member) within an organization can be set to one of the following states: active or inactive.  The value MUST be set to the appropriate term string value:

| Term | IRI |
| ------  | --- | 
| Active | http://purl.imsglobal.org/vocab/lis/v2/status#Active |
| Inactive | http://purl.imsglobal.org/vocab/lis/v2/status#Inactive |

<a name="contributors" />

### 11.0 Contributors
The following Caliper Working Group participants contributed to the writing of this specification:

#### Authors
| Name | Organization |
| ------ | --------- |
| Anthony Whyte | University of Michigan |
| Viktor Haag | D2L |
| Wes LaMarche | ACT |

#### Editors
| Name | Organization |
| ------ | --------- |
| Anthony Whyte | University of Michigan |
| Steven Erickson | Unicon |

<a name="reference" />

### 12.0 References

<a name="jsonldSyntax" />

__JSON-LD Syntax__  W3C.  M. Sporny, D. Longley, G. Kellog, M. Lanthaler and N. Lindström.  JSON-LD 1.1.  A JSON-based Serialization for Linked Data. 15 February 2017.  URL: http://json-ld.org/spec/latest/json-ld/

<a name="jsonldProcessing" />

__JSON-LD Processing__  D. Longley, G. Kellog, M. Lanthaler, M. Sporny.  JSON-LD 1.1 Processing Algorithms and API.  15 February 2017.  URL: http://json-ld.org/spec/latest/json-ld-api/

<a name="linkedData" />

__Linked Data__  Tim Berners-Lee.  "Linked Data."  W3C internal document.  July 2006, rev. June 2009.  URL: https://www.w3.org/DesignIssues/LinkedData.html

<a name="lti" />

__LTI__  TODO

<a name="rfc2119" />

__RFC 2119__ IETF.  S. Bradner. "Key words for use in RFCs to Indicate Requirement Levels." March 1997. URL: https://tools.ietf.org/html/rfc2119

<a name="rfc3987" />

__RFC 3987__ IETF. M. Duerst and M. Suignard.  "Internationalized Resource Identifiers (IRIs).  January 2005.  URL: https://www.ietf.org/rfc/rfc3987.txt

<a name="rfc4122" />

__RFC 4122__ IETF. P. Leach, M. Mealling and R. Salz.  "A Universally Unique Identifier (UUID) URN Namespace."  July 2005.  URL: https://tools.ietf.org/html/rfc4122

<a name="rfc6750 />

__RFC 6750__ IETF.  TODO Add reference

<a name="caliperWhitepaper" />

__White paper__  IMS Global Learning Consortium.  "Learning Measurement for Analytics Whitepaper \[sic\]."  August 2013.  URL: https://www.imsglobal.org/sites/default/files/caliper/IMSLearningAnalyticsWP.pdf

__WordNet__  Princeton University.  WordNet®.  A lexical database for English. 2010.  URL: https://wordnet.princeton.edu/