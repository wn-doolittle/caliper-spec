<h2>Caliper Analytics<sup>TM</sup> Specification, version 1.1</h2>
<h2>IMS Global Learning Consortium, Inc.<h2>

## IPR and Distribution Notices
Recipients of this document are requested to submit, with their comments, notification of any relevant patent claims or other intellectual property rights of which they may be aware that might be infringed by any implementation of the specification set forth in this document, and to provide supporting documentation.

IMS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on IMS’s procedures with respect to rights in IMS specifications can be found at the IMS Intellectual Property Rights web page: [http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Copyright © 2016 IMS Global Learning Consortium. All Rights Reserved.

Use of this specification to develop products or services is governed by the license with IMS found on the IMS website: [http://www.imsglobal.org/license.html](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Permission is granted to all parties to use excerpts from this document as needed in producing requests for proposals.

The limited permissions granted above are perpetual and will not be revoked by IMS or its successors or assigns.

THIS SPECIFICATION IS BEING OFFERED WITHOUT ANY WARRANTY WHATSOEVER, AND IN PARTICULAR, ANY WARRANTY OF NONINFRINGEMENT IS EXPRESSLY DISCLAIMED. ANY USE OF THIS SPECIFICATION SHALL BE MADE ENTIRELY AT THE IMPLEMENTER'S OWN RISK, AND NEITHER THE CONSORTIUM, NOR ANY OF ITS MEMBERS OR SUBMITTERS, SHALL HAVE ANY LIABILITY WHATSOEVER TO ANY IMPLEMENTER OR THIRD PARTY FOR ANY DAMAGES OF ANY NATURE WHATSOEVER, DIRECTLY OR INDIRECTLY, ARISING FROM THE USE OF THIS SPECIFICATION.

## Table of Contents
* 1.0 [Introduction](#introduction)
  * 1.1 [Namespaces](#namespaces)
  * 1.2 [Definitions](#definitions)
  * 1.3 [Terminology](#terminology)
* 2.0 [Data and Semantic Interoperability](#interoperability)
* 3.0 [Information Model](#infomodel)
* 4.0 [Profiles](#caliperProfiles)
	* 4.1 [Basic Profile](#basicProfile)
	* 4.2 [Annotation Profile](#annotationProfile)
	* 4.3 [Assignable Profile](#assignableProfile)
	* 4.4 [Assessment Profile](#assessmentProfile)
	* 4.6 [Forum Profile](#forumProfile)
	* 4.7 [Media Profile](#mediaProfile)
	* 4.8 [Outcome Profile](#outcomeProfile)
	* 4.9 [Reading Profile](#readingProfile)
	* 4.10 [Session Profile](#sessionProfile)
* 5.0 [Events](#events)
* 6.0 [Actions](#actionVocabulary)
* 7.0 [Entities](#entities)   
* 8.0 [Sensor API](#api)
* 9.0 [Transport](#transport)
    * 9.1 [Envelope](#envelope)
	* 9.2 [Endpoints](#endpoints)
* 10.0 [Contributors](#contributors)
* [Appendix A: Caliper Events](#appendixEvents)
	* [AnnotationEvent](#annotationEvent)
	* [AssessmentEvent](#assessmentEvent)
	* [AssessmentItemEvent](#assessmentItemEvent)
    * [AssignableEvent](#assignableEvent)
	* [ForumEvent](#ForumEvent)
	* [MediaEvent](#mediaEvent)
	* [MessageEvent](#messageEvent)
	* [NavigationEvent](#navigationEvent)
	* [OutcomeEvent](#outcomeEvent)
	* [SessionEvent](#sessionEvent)
	* [ThreadEvent](#ThreadEvent)
	* [ViewEvent](#viewEvent)
* [Appendix B: Caliper Actions](#appendixActions)
* [Appendix C: Caliper Entities](#appendixEntities)
	* [Agent](#agent)
	* [Annotation](#annotation)
	* [Assessment](#assessment)
    * [AssessmentItem](#assessmentItem)
	* [AssignableDigitalResource](#assignableDigitalResource)
	* [Attempt](#attempt)
	* [AudioObject](#audioObject)
	* [BookmarkAnnotation](#bookmarkAnnotation)
	* [Chapter](#chapter)
	* [Collection](#collection)
	* [CourseOffering](#courseOffering)
    * [CourseSection](#courseSection)
    * [DigitalResource](#digitalResource)
    * [DigitalResourceCollection](#digitalResourceCollection)
    * [Document](#document)
    * [FillinBlankResponse](#fillinBlankResponse)
    * [Forum](#forum)
    * [Frame](#frame)
    * [Group](#group)
    * [HighlightAnnotation](#highlightAnnotation)
    * [ImageObject](#imageObject)
    * [LearningObjective](#learningObjective)
    * [LtiSession](#ltiSession) 
    * [MediaLocation](#mediaLocation)
    * [MediaObject](#mediaObject)
    * [Membership](#membership)
    * [Message](#message)
    * [MultipleChoiceResponse](#multipleChoiceResponse)
    * [MultipleResponseResponse](#multipleResponseResponse)
	* [Organization](#organization)
	* [Page](#page)
	* [Person](#person)
	* [Response](#response)
	* [Result](#result)
	* [Session](#session)
	* [SharedAnnotation](#sharedAnnotation)
	* [SelectTextResponse](#selectTextResponse)
	* [SoftwareApplication](#softwareApplication)
    * [TagAnnotation](#tagAnnotation)
    * [TrueFalseResponse](#trueFalseResponse)
	* [Thread](#thread)
	* [VideoObject](#videoObject)
    * [WebPage](#webpage)
* [Appendix D: Caliper Person Roles and Statuses](#appendixRoles)
* [Appendix Z: Miscellaneous Classes](#appendixZ)
	* [Selector](#selector)
		* [TextPositionSelector](#textPositionSelector)
* [Revision History](#revisionHistory)
* [References](#references)

<a name="introduction"/>  
## 1.0. Introduction

TODO

<a name="namespaces"/>  
### 1.1 Namespaces
The Caliper information model references a number of terms derived from other ontologies.  Such terms along with those native to Caliper are identified with a prefix drawn from the list below that maps to the relevant namespace as, for example, the data type [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime).

| Prefix | Namespace | Description |
| ------ | --------- | ----------- |
| caliper | http://purl.imsglobal.org/caliper/v1/ | Caliper |
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

### 1.2 Terminology
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](#rfc2119).  A Sensor implementation that fails to implement a MUST/REQUIRED/SHALL requirement or fails to abide by a MUST NOT/SHALL NOT prohibition is considered non-conformant.  SHOULD/SHOULD NOT/RECOMMENDED statements constitute a best practice.  Ignoring a best practice does not violate conformance but a decision to disregard such guidance should be carefully considered.  MAY/OPTIONAL statements indicate that implementors are entirely free to choose whether or not to implement the option.

<a name="definitions"/>  
### 1.3 Definitions
__actor__: An actor specifies an external entity that interacts with a subject, a human user of a designed system, or some other system or hardware using services of the subject. An actor is the direct driver of an action. 

__action__: something done to accomplish a purpose

__blank node__: A locally-scoped identifier that is used to refer to a resource when a globally scoped identifier is either inappropriate, as in the case of transient data, or not provided.  A blank node is prefixed with an underscore (_) and is scoped to the document in which it is used (e.g., _:a1).

__context__: A  JSON-LD concept for mapping terms to an IRI.  JSON-LD contexts may be embedded in a document or referenced. 

__endpoint__: A specified set of operations and messages bound to a specific network protocol.  

__entity__:  An instance of a specified entity type.  An entity may represent a tangible object (person, school, building, ...) or concept (course, department,...).

__event__: A notable occurrence at a point in time.

__JSON-LD__: (JavaScript Object Notation for Linked Data) is a lightweight specification for using JSON to represent Linked Data.

__Linked Data__: A set of best practices for connecting structure data over the Web.  The term was coined by Tim Berners-Lee. 

__LTI__: Learning Tools Interoperability&reg; (LTI&reg;) is an IMS Global standard for integration of rich learning applications within educational environments.

__IRI__: The Internationalized Resource Identifier (IRI) extends the Uniform Resource Identifier (URI) scheme by using characters drawn from the Universal Character Set rather than ASCII.  The IRI is a globally scoped identifier used in linked data to refer to most nodes and properties.  An IRI reference may be absolute or relative to that of another absolute IRI.  In JSON-LD relative IRIs are resolved relative to the base IRI.

__ISO 8601__: Caliper time values are formatted per ISO 8601 with the addition of millisecond precision.  The format is yyyy-MM-ddTHH:mm:ss.SSSZ where 'T' separates the date from the time while 'Z' indicates that the time is in UTC. 

__profile__: metric profiles define the information model for caliper.  The caliper metric profiles are organized by activity. 

__sensor__: Software assets deployed within a learning application to facilitate interaction between the learning application and an event store

<a name="interoperability">
## 2.0 Data and Semantic Interoperability

TODO

structure, flow, pointers

<a name="infoModel">
## 3.0 Information Model

### Overview 

This section describes the concepts, relationships and constraints that specify the Caliper information model.  The Caliper information model applies semantic web concepts to events that occur in and around learning activities as well as activities that help facilitate learning.   These activities are organized by type and described by the following metric profiles:  

* Basic
* Annotation
* Assessment
* Assignable
* Forum
* Media
* Outcome
* Reading
* Session

A metric profile contains a description of:
 * the entities that participate in a learning activity
 * the possible actions that may be performed as part of the learning activity.
 * the events that may occur during an learning activity

Actors are capable of initiating an action such as a person, group, organization or software application.   Actors optionally may be assigned roles. Actors optionally may be members of groups or organizations.

Entities provide information about the objects, actors or resources that participate in an event.  Entities are further specified by contexts. The vocabularies for entities are drawn from a variety of sources.

Actions specify the set of potential interactions within the metric profile.

Conceptually, Caliper events in plan english are described as  _"ACTOR invokes an ACTION on an OBJECT at this TIME"_.  The events are recorded, along with contextual data, such as, location, date and time using JSON-LD.  JSON-LD is a light-weight linked data format that builds upon wide-spread adoption of JSON.  

<a name="caliperProfiles" />
## 4.0 Profiles
The Caliper Information Model is comprised of a number of activity profiles, each of which models a particular learning or supporting activity.  Each profile provides a common/structured vocabularly / concepts and terms for describing events such as annotating a document, starting an assessment or grading an outcome.  Extending the model involves adding a new profile or enhancing an existing one.

TODO: ADDITIONAL INTRO TEXT

[Basic](#basicProfile), [Annotation](#annotationProfile), [Assessment](#annotationProfile), [Assignable](#assignableProfile), [Forum](#forumProfile), [Media](#mediaProfile), [Outcome](#outcomeProfile), [Reading](#readingProfile), [Session](#sessionProfile)

<a name="basicProfile" />
### 4.1 Basic Profile
The Caliper Basic Profile models a minimally compliant [Event](#event) composed of an [actor](#actor), [action](#action), [object](#object) and [eventTime](#eventTime).  Any Caliper [action](#action) can be employed as the predicate.  All other [Event](#event) properties are considered optional. 

#### Supported Events
[Event](#Event)

#### Supported Actions
Any action included in the Caliper [actions](#actions) vocabulary can be employed to describe an actor's interaction with an object. 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime |
| -----  | ----- | ------ | ------ | ----------- |
| [Event](#assignableEvent) | [Person](#person) P1 | [created](#created) | [Group](#group) G1 | [dateTime](#dateTime) T1 |
| [Event](#assignableEvent) | [Person](#person) P1 | [modified](#created) | [Group](#group) G1 | [dateTime](#dateTime) T2 |
| [Event](#assignableEvent) | [Person](#person) P1 | [deleted](#deleted) | [Group](#group) G1 | [dateTime](#dateTime) T3 |

<a name="annotationProfile" />
### 4.2 Annotation Profile
The Caliper Annotation Profile models activities related to the annotation of digital content.

#### Supported Events
[AnnotationEvent](#annotationEvent), [ViewEvent](#ViewEvent)

#### Supported Actions
| Event | action(s) |
| -----  | --------- |
|[AnnotationEvent](#assignableEvent)  | [bookmarked](#bookmarked), [highlighted](#highlighted), [shared](#shared), [tagged](#tagged) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object and generated  entities
| Event | action | object | generated |
| -------  | -------- | -------- |  ----------- |
| [AnnotationEvent](#annotationEvent) | [bookmarked](#bookmarked) | [DigitalResource](#digitalResource) | [BookmarkAnnotation](#bookmarkAnnotation) |
| [AnnotationEvent](#annotationEvent) | [highlighted](#highlighted) | [DigitalResource](#digitalResource) | [HighlightAnnotation](#highlightAnnotation) |
| [AnnotationEvent](#annotationEvent) | [shared](#shared) | [DigitalResource](#digitalResource) | [SharedAnnotation](#sharedAnnotation) |
| [AnnotationEvent](#annotationEvent) | [tagged](#tagged) | [DigitalResource](#digitalResource) | [TagAnnotation](#tagAnnotation) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) | [Annotation](#annotation) | &nbsp; |

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime | generated |
| -----  | ----- | ------ | ------ | ----------- | ---------- |
| [AnnotationEvent](#annotationEvent) | [Person](#person) P1 | [highlighted](#highlighted) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T1 | [HighlightAnnotation](#highlightAnnotation) |
| [AnnotationEvent](#annotationEvent) | [Person](#person) P1 | [tagged](#tagged) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T2 | [TagAnnotation](#tagAnnotation) |
| [AnnotationEvent](#annotationEvent) | [Person](#person) P1 | [bookmarked](#bookmarked) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T3 | [BookmarkAnnotation](#bookmarkAnnotation) |

#### TODO
* Remove following actions from profile (not annotation actions): [attached](#attached), [classified](#classified), [described](#described), [identified](#identified), [linked](#linked), [questioned](#questioned), [subscribed](#subscribed).
* Q: is sharing a reference a form of annotation?
* Remove following actions from profile; migrate to future Evaluation profile: [disliked](#disliked), [liked](#liked), [ranked](#ranked), [recommended](#recommended)?
* Need a CommentAnnotation/MessageAnnotation entity for [commented](#commented) action OR use [Message](#message); consider deprecating [replied](#replied) action (redundant given [replyTo](#replyTo).

<a name="assessmentProfile" />
### 4.4 Assessment Profile
The Caliper Assessment Profile models assessment-related activities including interactions with individual assessment items.  

#### Supported Events
[AssessmentEvent](#assessmentEvent), [AssessmentItemEvent](#assessmentItemEvent) , [NavigationEvent](#navigationEvent),  [ViewEvent](#ViewEvent)

#### Supported Actions
| Event | action(s) |
| -----  | --------- |
| [AssessmentEvent](#assessmentEvent) | [started](#started), [paused](#paused), [restarted](#restarted), [submitted](#submitted) |
|  [AssessmentItemEvent](#assessmentItemEvent) | [started](#started), [skipped](#skipped), [completed](#completed)  |
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object, generated, target and referrer entities
| Event | action | object | generated | target | referrer |
| ----- | ------ | ------ | ----------- | ------ | ------- |
|  [AssessmentEvent](#assessmentEvent) | [started](#started), [paused](#paused), [restarted](#restarted) | [Assessment](#assessment) | [Attempt](#attempt) | &nbsp; | &nbsp; |
|  [AssessmentEvent](#assessmentEvent) | [submitted](#submitted) | [Attempt](#attempt) | &nbsp; | &nbsp; | &nbsp; |
|  [AssessmentItemEvent](#assessmentItemEvent) | [started](#started), [skipped](#skipped) | [Assessment](#assessment) | [Attempt](#attempt) | &nbsp; | [AssessmentItem](#assessmentItem) |
|  [AssessmentItemEvent](#assessmentItemEvent) | [completed](#completed) | [Attempt](#attempt) | &nbsp; | &nbsp; | &nbsp; |
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) | [Assessment](#assessment), [AssessmentItem](#assessmentItem) | &nbsp; | &nbsp; | [DigitalResource](#digitalResource) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) | [Assessment](#assessment), [AssessmentItem](#assessmentItem) | &nbsp; | &nbsp; | &nbsp; 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime | generated |
| -----  | ----- | ------ | ------ | ----------- | ---------- |
| [NavigationEvent](#navigationEvent) | [Person](#person) P1 | [navigatedTo](#navigatedTo) | [Assessment](#assessment) A1 | [dateTime](#dateTime) T1 | &nbsp; |
| [AssessmentEvent](#assessmentEvent)  | [Person](#person) P1 | [started](#started) | [Assessment](#assessment) A1 | [dateTime](#dateTime) T2 | [Attempt](#attempt) A1A1 |
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) P1 | [started](#started) | [AssessmentItem](#assessmentItem) I1 | [dateTime](#dateTime) T3 | [Attempt](#attempt) I1A1 | 
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) P1 | [completed](#completed) | [Attempt](#attempt) I1A1 | [dateTime](#dateTime) T4 | [Response](#response) R1 |
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) P1 | [skipped](#skipped) | [AssessmentItem](#assessmentItem) I2 | [dateTime](#dateTime) T5 | &nbsp; |
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) P1 | [started](#started) | [AssessmentItem](#assessmentItem) I3 | [dateTime](#dateTime) T6 | [Attempt](#attempt) I3A1 | 
| [AssessmentItemEvent](#assessmentItemEvent) | [Person](#person) P1 | [completed](#completed) |  [Attempt](#attempt) I3A1  | [dateTime](#dateTime) T7 | [Response](#response) R2 |
| [AssessmentEvent](#assessmentEvent)  | [Person](#person) P1 | [submitted](#submitted) | [Attempt](#attempt) A1A1 | [dateTime](#dateTime) T8 | &nbsp; |

<a name="assignableProfile" />
### 4.3 Assignable Profile
The Assignable Profile provides coverage for all activity types that can be assigned to a learner for completion according to specific criteria.  ~~Assignable is an interface that is implemented by the AssignableDigitalResource.  Any Entity can implement AssignableDigitalResource and become “assignable”.~~

#### Supported Events
[AssignableEvent](#assignableEvent), [NavigationEvent](#navigationEvent), [ViewEvent](#ViewEvent)

#### Supported Actions
| Event | action(s) |
| -----  | --------- |
|[AssignableEvent](#assignableEvent)  | [activated](#activated), [deactivated](#deactivated), [started](#started), [completed](#completed) |
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object, generated, target and referrer entities
| Event | action | object | generated | target | referrer |
| ----- | -------| ------ | ----------- | ------ | ------- |
|  [AssignableEvent](#assignableEvent)  | [activated](#activated), [deactivated](#deactivated) | [DigitalResource](#digitalResource) | &nbsp;  | &nbsp; | &nbsp; |
|  [AssignableEvent](#assignableEvent)  | [started](#started)| [DigitalResource](#digitalResource) | [Attempt](#attempt) | &nbsp; | &nbsp; |
|  [AssignableEvent](#assignableEvent)  | [completed](#completed) | [Attempt](#attempt)| &nbsp; | &nbsp; | &nbsp; |
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | [DigitalResource](#digitalResource) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | &nbsp; 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime | generated |
| -----  | ----- | ------ | ------ | ----------- | ---------- |
| [AssignableEvent](#assignableEvent) | [Person](#person) P1 | [activated](#activated) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T1 | &nbsp; |
| [NavigationEvent](#navigationEvent) | [Person](#person) P2 | [navigatedTo](#navigatedTo) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T2 | &nbsp; |
| [AssignableEvent](#assignableEvent) | [Person](#person) P2 |  [started](#started) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T3 | [Attempt](#attempt) I1A1 |
| [AssignableEvent](#assignableEvent) | [Person](#person) P2 |  [completed](#completed) | [Attempt](#attempt) I1A1  | [dateTime](#dateTime) T4 | &nbsp; |
| [AssignableEvent](#assignableEvent) | [Person](#person) P1 | [deactivated](#deactivated) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T5 | &nbsp; |

#### TODO
* Do we need to add a submitted action?

<a name="forumProfile" />
### 4.6 Forum Profile
The online forum is a core capability of many learning management systems.  Forums typically encompass one or more topics to which actors can subscribe, post messages and reply to other messages if a threaded discussion is permitted.  The profile leverages a number of Caliper [Event](#event) types to describe users participating in online forum communities.

#### Supported Events
[ForumEvent](#forumEvent),  [MessageEvent](#messageEvent),  [NavigationEvent](#navigationEvent), [ThreadEvent](#threadEvent), [ViewEvent](#ViewEvent)

#### Supported Actions
| Event | action(s) |
| -----  | --------- |
| [ForumEvent](#forumEvent) | [subscribed](#subscribed), [unsubscribed](#unsubscribed) |
| [MessageEvent](#messageEvent) | [posted](#posted), [markedAsRead](#markedAsRead), [markedAsUnRead](#markedAsUnRead)|
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) |
| [ThreadEvent](#threadEvent)|[markedAsRead](#markedAsRead), [markedAsUnRead](#markedAsUnRead) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object, generated, target and referrer entities
| Event | object | generated | target | referrer |
| ----- | ------ | ----------- | ------ | ------- |
| [ForumEvent](#forumEvent) | [Forum](#forum) | &nbsp; | &nbsp; | &nbsp; |
| [MessageEvent](#messageEvent) | [Message](#message) | &nbsp; | &nbsp; | &nbsp; |
| [ThreadEvent](#threadEvent) | [Thread](#thread) | &nbsp; | &nbsp; | &nbsp; |
| [NavigationEvent](#navigationEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | [DigitalResource](#digitalResource) |
| [ViewEvent](#viewEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | &nbsp; 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information are assumed in example sequence*.
 
| Event | actor | action | object | eventTime |
| -----  | ----- | ------ | ------ | ----------- |
| [NavigationEvent](#navigationEvent) | [Person](#person) P1 | [navigatedTo](#navigatedTo) | [Forum](#forum) F1 | [dateTime](#dateTime) T1 |
| [ForumEvent](#forumEvent) | [Person](#person) P1 | [subscribed](#subscribed) | [Forum](#forum) F1 | [dateTime](#dateTime) T2 |
| [ViewEvent](#viewEvent)| [Person](#person) P1 | [viewed](#viewed) | [Thread](#thread) Th1 isPartOf F1 | [dateTime](#dateTime) T3 |
| [ViewEvent](#viewEvent) | [Person](#person) P1 | [viewed](#viewed) | [Message](#message) M1 isPartOf Th1 | [dateTime](#dateTime) T4 |
| [MessageEvent](#messageEvent) | [Person](#person) P1 | [posted](#posted) | [Message](#message) M2 replyTo M1 | [dateTime](#dateTime) T5 |
| [ThreadEvent](#threadEvent)| [Person](#person) P1 | [markedAsRead](#markedAsRead) | [Thread](#thread) Th1 isPartOf F1 | [dateTime](#dateTime) T6 |

<a name="mediaProfile" />
### 4.7 Media Profile
The Caliper Media Profile models interactions between learners and rich content such as audio, images and video.  The profile is provisioned with a number of media-related entities including [AudioObject](#audioObject), [ImageObject](#audioObject), and [VideoObject](#videoObject), each subclassed from a generic [MediaObject](#mediaObject).  The [MediaLocation](#mediaLocation) entity provides an [index](#index) property . . .  [TODO]

#### Supported Events
[MediaEvent](#mediaEvent), [NavigationEvent](#navigationEvent), [ViewEvent](#ViewEvent)

#### Supported actions
| Event | action | 
| -----  | ------ |
| [MediaEvent](#mediaEvent) | [started](#started), [paused](#paused), [resumed](#resumed), [forwardedTo](#forwardedTo), [jumpedTo](#jumpedTo), [rewound](#rewound), [ended](#ended), [changedResolution](#changedResolution), [changedSize](#changedSize), [changedSpeed](#changedSpeed), [changedVolume](#changedVolume), [enabledClosedCaptioning](#enabledClosedCaptioning), [disabledClosedCaptioning](#disabledClosedCaptioning), [enteredFullScreen](#enteredFullScreen), [exitedFullScreen](#exitedFullScreen), [muted](#muted), [unmuted](#unmuted), [openedPopout](#openedPopout), [closedPopout](#closedPopout) |
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object, generated, target and referrer entities
| Event | object | generated | target | referrer |
| ----- | ------ | ----------- | ------ | ------- |
| [MediaEvent](#mediaEvent) | [MediaObject](#mediaObject), [AudioObject](#audioObject), [ImageObject](#audioObject), [VideoObject](#videoObject), [MediaLocation](#mediaLocation) | &nbsp; |~~[MediaLocation](#mediaLocation)~~ | &nbsp; |
| [NavigationEvent](#navigationEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | [DigitalResource](#digitalResource) |
| [ViewEvent](#ViewEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | &nbsp; 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information are assumed in example sequence*.
 
| Event | actor | action | object | eventTime | target |
| -----  | ----- | ------ | ------ | ----------- | ------ |
| [NavigationEvent](#navigationEvent) | [Person](#person) P1 | [navigatedTo](#navigatedTo) | [VideoObject](#videoObject) V1 | [dateTime](#dateTime) T1 | &nbsp; |
| [MediaEvent](#mediaEvent) | [Person](#person) P1 | [started](#started) | [VideoObject](#videoObject) V1 | [dateTime](#dateTime) T2 | [MediaLocation](#mediaLocation) L1 |
| [MediaEvent](#mediaEvent) | [Person](#person) P1 | [changedVolume](#changedVolume) | [VideoObject](#videoObject) V1 | [dateTime](#dateTime) T3 |  [MediaLocation](#mediaLocation) L2 |
| [MediaEvent](#mediaEvent) | [Person](#person) P1 | [paused](#paused) | [VideoObject](#videoObject) V1 | [dateTime](#dateTime) T4 |  [MediaLocation](#mediaLocation) L3 |
| [MediaEvent](#mediaEvent) | [Person](#person) P1 | [resumed](#resumed) | [VideoObject](#videoObject) V1 | [dateTime](#dateTime) T5 |  [MediaLocation](#mediaLocation) L4 |
| [MediaEvent](#mediaEvent) | [Person](#person) P1 | [ended](#ended) | [VideoObject](#videoObject) V1 | [dateTime](#dateTime) T6 |  [MediaLocation](#mediaLocation) L5 |

#### TODO
* Confirm that MediaLocation should be utilized as the object of the interaction rather than the target.

<a name="outcomeProfile" />
### 4.8 Outcome Profile
The Caliper Outcome Profile models grading activities performed by an [Agent](#agent), typically a [Person](#person) or a [SoftwareApplication](#softwareApplication).  The object of a grading action is an [Attempt](#attempt) from which a [Result](#result) is generated.  A [Result](#result) can then be viewed.

#### Supported Events
[OutcomeEvent](#outcomeEvent), [ViewEvent](#ViewEvent)

#### Supported actions
| Event | action(s) |
| -----  | --------- |
| [OutcomeEvent](#outcomeEvent) | [graded](#graded) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object, generated, target and referrer entities
| Event | object | generated | target | referrer |
| ----- | ------ | ----------- | ------ | ------- |
| [OutcomeEvent](#mediaEvent) | [Attempt](#attempt) | [Result](#result) | &nbsp; | &nbsp; |
| [ViewEvent](#ViewEvent) | [Result](#result) | &nbsp; | &nbsp; | &nbsp; 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime | generated |
| -----  | ----- | ------ | ------ | ----------- | ---------- |
|  [OutcomeEvent](#outcomeEvent) | [Person](#person) P1 | [graded](#graded) | [Attempt](#attempt) A1 | [dateTime](#dateTime) T1 | [Result](#result) R1 |
| [ViewEvent](#viewEvent)| [Person](#person) P2 | [viewed](#viewed) | [Result](#result) R1 | [dateTime](#dateTime) T2 | &nbsp; |

<a name="readingProfile" />
### 4.9 Reading Profile
The Caliper Reading Profile models activities associated with reading textual content.  The profile is provisioned with a number of entities representing digital content such as [Document](#document), [Chapter](#chapter), [Page](#page), [WebPage](#webPage) and [Frame](#frame), each subclassed from [DigitalResource](#digitalResource).

#### Supported Events
[NavigationEvent](#navigationEvent), [ViewEvent](#ViewEvent)

#### Supported actions
| Event | action(s) |
| -----  | --------- |
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object, generated, target and referrer entities
| Event | object | generated | target | referrer |
| ----- | ------ | ----------- | ------ | ------- |
| [NavigationEvent](#navigationEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | [DigitalResource](#digitalResource) |
| [ViewEvent](#ViewEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | &nbsp; 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime | referrer |
| -----  | ----- | ------ | ------ | ----------- | ---------- |
| [NavigationEvent](#navigationEvent) | [Person](#person) P1 | [navigatedTo](#navigatedTo) | [DigitalResource](#digitalResource) D2 | [dateTime](#dateTime) T1 | [DigitalResource](#digitalResource) D1 |
| [ViewEvent](#viewEvent) | [Person](#person) P1 | [viewed](#viewed) | [DigitalResource](#digitalResource) D2 | [dateTime](#dateTime) T2 | &nbsp; |

<a name="sessionProfile" />
### 4.10 Session Profile
The Caliper Session Profile models activities associated with a user session established by a [Person](#person), interacting with a [SoftwareApplication](#softwareApplication).  A single [SessionEvent](#sessionEvent) is modeled along with a small set of supported actions.

#### Supported Events
[SessionEvent](#sessionEvent) 

#### Supported actions
| Event | action(s) |
| -----  | --------- |
|  [SessionEvent](#sessionEvent) | [loggedIn](#loggedIn), [loggedOut](#loggedIn), [timedOut](#timedOut)  |

#### Supported object, session and federatedSession entities
| Event | action | object | session | federatedSession |
| ----- | ------ | ------ | -------- | ------------------ |
| [SessionEvent](#sessionEvent) | [loggedIn](#loggedIn), [loggedOut](#loggedIn) | [SoftwareApplication](#softwareApplication)  | [Session]([#session) | [LtiSession]([#ltiSession)  |
| [SessionEvent](#sessionEvent) | [timedOut](#timedOut) | [Session]([#session)  | &nbsp; | [LtiSession]([#ltiSession) |

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime | session |
| -----  | ----- | ------ | ------ | ----------- | ---------- |
| [SessionEvent](#sessionEvent) | [Person](#person) P1 | [loggedIn](#loggedIn) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T1 |  [Session](#session) |
| [SessionEvent](#sessionEvent) | [Person](#person) P1 | [loggedOut](#loggedIn) | [DigitalResource](#digitalResource) D1 | [dateTime](#dateTime) T2 | [Session](#session) |

#### TODO
* Discuss [LtiSession](#ltiSession)

<a name="events" />
## 5.0 Events

A Caliper Event is a generic class that represents the interaction between an [actor](#actor) and an [object](#object) at a specific moment in time and within the bounds of a specified context. For enhanced specificity implementors SHOULD utilize the several subclasses of Event rather than instantiating instances of the Event class itself.

For an Event to be minimally compliant it MUST specify an [actor](#actor), [action](#action), [object](#object) and an [eventTime](#eventTime).

An Event is immutable.

#### TODO
* should we recommend that the id be in the form of a hash generated by a hash function?

#### Supported actions
TODO List all Actions?

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | If a generic Event is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Event; otherwise the value MUST be assigned the IRI appropriate for the subclass utilized, e.g., http://purl.imsglobal.org/caliper/v1/NavigationEvent.  |
| actor  | [Agent](#agent) | The Agent who initiated or is the subject of this Event, typically a [Person]([#person), [Organization]([#organization) or [SoftwareApplication]([#softwareapplication).  Note that Agent is a generic type that is subclassed for greater type specificity.  Utilize Agent only if no suitable subclass exists to represent the object.  |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The action or predicate that binds the actor or subject to the object.  The value range is limited to the actions defined in this specification.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed |
| object | [Entity](#entity) | Entity is a generic type that is subclassed for greater type specificity.  Utilize Entity only if no suitable subclass exists to represent the object. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | &nbsp; | &nbsp; |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.  |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| The current Session. | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Subclasses
[AnnotationEvent](#annotationEvent), [AssignableEvent](#assignableEvent), [AssignmentEvent](#assignmentEvent), [AssignmentItemEvent](#assignmentItemEvent), [ForumEvent](#forumEvent), [MediaEvent](#mediaEvent), [MessageEvent](#messageEvent), [NavigationEvent](#navigationEvent), [OutcomeEvent](#outcomeEvent), [ReadingEvent](#readingEvent), [SessionEvent](#sessionEvent), [ThreadEvent](#threadEvent), [ViewEvent](#viewEvent)

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/Event",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Created",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/resources/123",
    "@type": "http://purl.imsglobal.org/caliper/v1/Document",
    "name": "Course Syllabus",
    "dateCreated": "2016-11-12T07:15:00.000Z",
    "version": "1"
  },
  "eventTime": "2016-11-15T10:15:00.000Z"
}
```

<a name="actionVocabulary"/>   
## 6.0 Actions
TODO DESCRIPTION

natural language challenges
past-tense form utilized
action can involve the change of a particular characteristic (e.g., resolution, size, speed, volume)

| Label | IRI | WordNet Gloss |
| ------ | --- | ------------- |
| <a name="abandoned" />abandoned | [http://purl.imsglobal.org/vocab/caliper/v1/action#Abandoned](http://purl.imsglobal.org/vocab/caliper/v1/action#Abandoned) | [forsake, leave behind](http://wordnet-rdf.princeton.edu/wn31/202232813-v) |
| <a name="activated" />activated | [http://purl.imsglobal.org/vocab/caliper/v1/action#Activated](http://purl.imsglobal.org/vocab/caliper/v1/action#Activated) | [make active or more active](http://wordnet-rdf.princeton.edu/wn31/200191014-v) |
| <a name="added" />added | [http://purl.imsglobal.org/vocab/caliper/v1/action#Added](http://purl.imsglobal.org/vocab/caliper/v1/action#Added) | [make an addition (to); join or combine or unite with others; increase the quality, quantity, size or scope of](http://wordnet-rdf.princeton.edu/wn31/200182551-v) |
| <a name="attached" />attached | [http://purl.imsglobal.org/vocab/caliper/v1/action#Attached](http://purl.imsglobal.org/vocab/caliper/v1/action#Attached) | [cause to be attached](http://wordnet-rdf.princeton.edu/wn31/201299048-v) |
| <a name="bookmarked" />bookmarked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Bookmarked](http://purl.imsglobal.org/vocab/caliper/v1/action#Bookmarked) | An IRI that marks a location of interest in a DigitalResource that is recorded for later retrieval.  |
| <a name="changedResolution" />changed resolution | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedResolution](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedResolution) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of [the number of pixels per square inch on a computer-generated display](http://wordnet-rdf.princeton.edu/wn31/111526370-n) |
| <a name="changedSize" />changed size | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSize](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSize) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of [the physical magnitude of something](http://wordnet-rdf.princeton.edu/wn31/105106204-n) |
| <a name="changedSpeed" />changed speed | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSpeed](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSpeed) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of the [rate at which something happens](http://wordnet-rdf.princeton.edu/wn31/105065291-n) |
| <a name="changedVolume" />changed volume | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedVolume](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedVolume) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) of [the magnitude of sound &#40;usually in a specified direction&#41;](http://wordnet-rdf.princeton.edu/wn31/104997456-n) |
| <a name="classified" />classified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Classified](http://purl.imsglobal.org/vocab/caliper/v1/action#Classified) | [assign to a class or kind](http://wordnet-rdf.princeton.edu/wn31/200741667-v) |
| <a name="closedPopout" />closed popout | [http://purl.imsglobal.org/vocab/caliper/v1/action#ClosedPopout](http://purl.imsglobal.org/vocab/caliper/v1/action#ClosedPopout) | [close or shut](http://wordnet-rdf.princeton.edu/wn31/201349660-v) a video popout |
| <a name="commented" />commented | [http://purl.imsglobal.org/vocab/caliper/v1/action#Commented](http://purl.imsglobal.org/vocab/caliper/v1/action#Commented) | [make or write a comment on](http://wordnet-rdf.princeton.edu/wn31/201060446-v) |
| <a name="completed" />completed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Completed](http://purl.imsglobal.org/vocab/caliper/v1/action#Completed) | [come or bring to a finish or an end](http://wordnet-rdf.princeton.edu/wn31/200485097-v) |
| <a name="created" />created | [http://purl.imsglobal.org/vocab/caliper/v1/action#Created](http://purl.imsglobal.org/vocab/caliper/v1/action#Created) | [make or cause to be or to become](http://wordnet-rdf.princeton.edu/wn31/201620211-v) |
| <a name="deactivated" />deactivated | [http://purl.imsglobal.org/vocab/caliper/v1/action#Deactivated](http://purl.imsglobal.org/vocab/caliper/v1/action#Deactivated) | [make inactive](http://wordnet-rdf.princeton.edu/wn31/200191849-v); inverse of activated |
| deleted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted](http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted) | [wipe out digitally](http://wordnet-rdf.princeton.edu/wn31/201001860-v) |
| <a name="described" />described | [http://purl.imsglobal.org/vocab/caliper/v1/action#Described](http://purl.imsglobal.org/vocab/caliper/v1/action#Described) | [give a description of](http://wordnet-rdf.princeton.edu/wn31/200989103-v) |
| <a name="disabledClosedCaptioning" />disabled closed captioning | [http://purl.imsglobal.org/vocab/caliper/v1/action#DisabledClosedCaptioning](http://purl.imsglobal.org/vocab/caliper/v1/action#DisabledClosedCaptioning) | [render unable to perform](http://wordnet-rdf.princeton.edu/wn31/200513267-v) the visual display of a textual transcription of audio output |
| <a name="disliked" />disliked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Disliked](http://purl.imsglobal.org/vocab/caliper/v1/action#Disliked) | [have or feel a dislike or distaste for](http://wordnet-rdf.princeton.edu/wn31/201780648-v); inverse of liked |
| <a name="enabledClosedCaptioning" />enabled closed captioning | [http://purl.imsglobal.org/vocab/caliper/v1/action#EnabledClosedCaptioning](http://purl.imsglobal.org/vocab/caliper/v1/action#EnabledClosedCaptioning) | [render capable or able](http://wordnet-rdf.princeton.edu/wn31/200513958-v) the visual display of a textual transcription of audio output |
| <a name="ended" />ended | [http://purl.imsglobal.org/vocab/caliper/v1/action#Ended](http://purl.imsglobal.org/vocab/caliper/v1/action#Ended) | [bring to an end or halt](http://wordnet-rdf.princeton.edu/wn31/200353480-v) |
| <a name="enteredFullscreen" />entered full screen | [http://purl.imsglobal.org/vocab/caliper/v1/action#EnteredFullscreen](http://purl.imsglobal.org/vocab/caliper/v1/action#EnteredFullscreen) | [to come or go into](http://wordnet-rdf.princeton.edu/wn31/202020375-v) a view mode that utilizes all the available display surface of a screen |
| <a name="exitedFullscreen" />exited full screen | [http://purl.imsglobal.org/vocab/caliper/v1/action#ExitedFullscreen](http://purl.imsglobal.org/vocab/caliper/v1/action#ExitedFullscreen) | [move out of or depart from](http://wordnet-rdf.princeton.edu/wn31/202019450-v) a view mode that utilizes all the available display surface of a screen |
| <a name="forwardedTo" />forwarded to | [http://purl.imsglobal.org/vocab/caliper/v1/action#ForwardedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#ForwardedTo) | [send or ship onward](http://wordnet-rdf.princeton.edu/wn31/201959367-v) |
| <a name="graded" />graded | [http://purl.imsglobal.org/vocab/caliper/v1/action#Graded](http://purl.imsglobal.org/vocab/caliper/v1/action#Graded) | [assign a grade or rank to, according to one's evaluation](http://wordnet-rdf.princeton.edu/wn31/200659399-v) |
| <a name="hid" />hid | [http://purl.imsglobal.org/vocab/caliper/v1/action#Hid](http://purl.imsglobal.org/vocab/caliper/v1/action#Hid) |[prevent from being seen or discovered](http://wordnet-rdf.princeton.edu/wn31/202149298-v) |
| <a name="highlighted" />highlighted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Highlighted](http://purl.imsglobal.org/vocab/caliper/v1/action#Highlighted) | [move into the foreground to make more visible or prominent](http://wordnet-rdf.princeton.edu/wn31/200515150-v) |
| <a name="identified" />identified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Identified](http://purl.imsglobal.org/vocab/caliper/v1/action#Identified) | [recognize as being; establish the identity of someone or something](http://wordnet-rdf.princeton.edu/wn31/200620568-v) |
| <a name="jumpedTo" />jumped to | [http://purl.imsglobal.org/vocab/caliper/v1/action#JumpedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#JumpedTo) | [pass abruptly from one state or topic to another](http://wordnet-rdf.princeton.edu/wn31/200561468-v) |
| <a name="liked" />liked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Liked](http://purl.imsglobal.org/vocab/caliper/v1/action#Liked) | [be fond of](http://wordnet-rdf.princeton.edu/wn31/201780873-v) |
| <a name="linked" />linked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Linked](http://purl.imsglobal.org/vocab/caliper/v1/action#Linked) | [connect, fasten, or put together two or more pieces](http://wordnet-rdf.princeton.edu/wn31/201357376-v) |
| <a name="loggedIn" />logged in | [http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn) | [enter a computer or software application](http://wordnet-rdf.princeton.edu/wn31/202253955-v) |
| <a name="loggedIn" />logged out | [http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut) | [exit a computer or software application](http://wordnet-rdf.princeton.edu/wn31/202254101-v) |
| <a name="markedAsRead" />marked as read | [http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead) | [mark: designate as if by a mark](http://wordnet-rdf.princeton.edu/wn31/200923709-v), [read: interpret something that is written or printed](http://wordnet-rdf.princeton.edu/wn31/200626756-v) |
| <a name="markedAsUnread" />marked as unread | [http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread) | inverse of markedAsRead |
| <a name="modified" />modified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Modified](http://purl.imsglobal.org/vocab/caliper/v1/action#Modified) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) |
| <a name="muted" />muted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Muted](http://purl.imsglobal.org/vocab/caliper/v1/action#Muted) | [deaden (a sound or noise)](http://wordnet-rdf.princeton.edu/wn31/mute-v) |
| <a name="navigated to" />navigated to | [http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo) | [direct the course; determine the direction of travelling](http://wordnet-rdf.princeton.edu/wn31/201935739-v) |
| <a name="openedPopout" />opened popout | [http://purl.imsglobal.org/vocab/caliper/v1/action#OpenedPopout](http://purl.imsglobal.org/vocab/caliper/v1/action#OpenedPopout) | [start to operate or function or cause to start operating or functioning](http://wordnet-rdf.princeton.edu/wn31/202431018-v) a video popout |
| <a name="paused" />paused | [http://purl.imsglobal.org/vocab/caliper/v1/action#Paused](http://purl.imsglobal.org/vocab/caliper/v1/action#Paused) | [cease an action temporarily](http://wordnet-rdf.princeton.edu/wn31/200781106-v) |
| <a name="posted" />posted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Posted](http://purl.imsglobal.org/vocab/caliper/v1/action#Posted) | [to cause to be directed or transmitted to another place](http://wordnet-rdf.princeton.edu/wn31/201033289-v)  |
| <a name="questioned" />questioned | [http://purl.imsglobal.org/vocab/caliper/v1/action#Questioned](http://purl.imsglobal.org/vocab/caliper/v1/action#Questioned) | [pose a question](http://wordnet-rdf.princeton.edu/wn31/200786670-v) |
| <a name="ranked" />ranked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Ranked](http://purl.imsglobal.org/vocab/caliper/v1/action#Ranked) | [assign a rank or rating to](http://wordnet-rdf.princeton.edu/wn31/200659723-v) |
| <a name="recommended" />recommended | [http://purl.imsglobal.org/vocab/caliper/v1/action#Recommended](http://purl.imsglobal.org/vocab/caliper/v1/action#Recommended) | [express a good opinion of](http://wordnet-rdf.princeton.edu/wn31/200884469-v) |
| <a name="removed" />removed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Removed](http://purl.imsglobal.org/vocab/caliper/v1/action#Removed) | [remove from sight](http://wordnet-rdf.princeton.edu/wn31/200181704-v) |
| <a name="reset" />reset | [http://purl.imsglobal.org/vocab/caliper/v1/action#Reset](http://purl.imsglobal.org/vocab/caliper/v1/action#Reset) | [set anew](http://wordnet-rdf.princeton.edu/wn31/200949623-v) |
| <a name="restarted" />restarted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Restarted](http://purl.imsglobal.org/vocab/caliper/v1/action#Restarted) | [take up or begin anew](http://wordnet-rdf.princeton.edu/wn31/200350758-v)|
| <a name="resumed" />resumed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Resumed](http://purl.imsglobal.org/vocab/caliper/v1/action#Resumed) | [take up or begin anew](http://wordnet-rdf.princeton.edu/wn31/200350758-v) |
| <a name="retrieved" />retrieved | [http://purl.imsglobal.org/vocab/caliper/v1/action#Retrieved](http://purl.imsglobal.org/vocab/caliper/v1/action#Retrieved) | [obtain or retrieve from a storage device; as of information on a computer](http://wordnet-rdf.princeton.edu/wn31/202253616-v) |
| <a name="reviewed" />reviewed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Reviewed](http://purl.imsglobal.org/vocab/caliper/v1/action#Reviewed) | [appraise critically](http://wordnet-rdf.princeton.edu/wn31/200857194-v) |
| <a name="rewound" />rewound | [http://purl.imsglobal.org/vocab/caliper/v1/action#Rewound](http://purl.imsglobal.org/vocab/caliper/v1/action#Rewound) | [wind up again](http://wordnet-rdf.princeton.edu/wn31/201524927-v)|
| <a name="searched" />searched | [http://purl.imsglobal.org/vocab/caliper/v1/action#Searched](http://purl.imsglobal.org/vocab/caliper/v1/action#Searched) | [try to locate or discover, or try to establish the existence of](http://wordnet-rdf.princeton.edu/wn31/201318273-v) |
| <a name="shared" />shared | [http://purl.imsglobal.org/vocab/caliper/v1/action#Shared](http://purl.imsglobal.org/vocab/caliper/v1/action#Shared) | [communicate](http://wordnet-rdf.princeton.edu/wn31/201065952-v) |
| <a name="showed" />showed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Showed](http://purl.imsglobal.org/vocab/caliper/v1/action#Showed) | [make visible or noticeable](http://wordnet-rdf.princeton.edu/wn31/202141597-v) |
| <a name="skipped" />skipped | [http://purl.imsglobal.org/vocab/caliper/v1/action#Skipped](http://purl.imsglobal.org/vocab/caliper/v1/action#Skipped) | [bypass](http://wordnet-rdf.princeton.edu/wn31/200618188-v) |
| <a name="started" />started | [http://purl.imsglobal.org/vocab/caliper/v1/action#Started](http://purl.imsglobal.org/vocab/caliper/v1/action#Started) | [set in motion, cause to start](http://wordnet-rdf.princeton.edu/wn31/200349400-v) |
| <a name="submitted" />submitted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Submitted](http://purl.imsglobal.org/vocab/caliper/v1/action#Submitted) | [hand over formally](http://wordnet-rdf.princeton.edu/wn31/202267560-v) |
| <a name="subscribed" />subscribed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed) | [ receive or obtain regularly](http://wordnet-rdf.princeton.edu/wn31/202214527-v) |
| <a name="tagged" />tagged | [http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged](http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged) | [attach a tag or label to](http://wordnet-rdf.princeton.edu/wn31/201591414-v) |
| <a name="timedOut" />timed out | [http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut](http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut) | Cancellation of a user session after a predetermined time interval has occurred without activity. |
| <a name="unmuted" />unmuted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Unmuted](http://purl.imsglobal.org/vocab/caliper/v1/action#Unmuted) | inverse of muted |
| <a name="unsubscribed" />unsubscribed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed) | inverse of subscribed |
| <a name="viewed" />viewed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed](http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed) |[look at carefully; study mentally](http://wordnet-rdf.princeton.edu/wn31/202134765-v) |

<a name="entities" />
## 7.0 Entities

A Caliper Entity is a generic class that is analogous to an [sdo:Thing](http://schema.org/Thing).  Entity is a generic type that is subclassed for greater type specificity.  Given that Entity represents a generic type it is RECOMMENDED that only subclasses of Entity be employed to represent nodes in the learning graph.

TODO: ADD ADDITIONAL INFO

#### Required properties
| Property | Type | Requirements |
| -------- | ---- | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An Entity SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an Entity MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | If a generic Entity is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Entity; otherwise the value MUST be assigned the IRI appropriate for the subclass, e.g., http://purl.imsglobal.org/caliper/v1/Person. |

#### Optional properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| name | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A word or phrase by which the [Entity](#entity) is known.  Analogous to [sdo:name](http://schema.org/name). |
| description | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A short representation of the [Entity](#entity) in written form.  Analogous to [sdo:description](http://schema.org/description). |
| dateCreated | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when the [Entity](#entity) was created or added to a data set.  Analogous to [sdo:dateCreated](http://schema.org/dateCreated). |
| dateModified | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted  date and time expressed with millisecond precision that represents when the [Entity](#entity) was last modified.  Analogous to [sdo:dateModified](http://schema.org/dateModified). |
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Entity. |

#### Subclasses
[Agent](#agent), [Annotation](#annotation), [Assessment](#assessment), [AssessmentItem](#assessmentItem), [AssignableDigitalResource](#assignableDigitalResource), [Attempt](#attempt), [AudioObject](#audioobject), [BookmarkAnnotation](#bookmarkAnnotation), [Chapter](#chapter), [Collection](#collection), [CourseOffering](#courseOffering), [CourseSection](#courseSection), [DigitalResource](#digitalResource), [Document](#document), [EpubChapter](#epubChapter), [EpubPart](#epubPart), [EpubSubChapter](#epubSubChapter), [EpubVolume](#epubVolume), [FillinBlankResponse](#fillinBlankResponse), [Frame](#frame), [Forum](#forum), [Group](#group), [HighlightAnnotation](#highlightAnnotation), [ImageObject](#imageobject), [LearningObjective](#learningObjective), [LtiSession](#ltiSession), [MediaLocation](#mediaLocation), [MediaObject](#mediaobject), [Membership](#membership), [Message](#message), [MultipleChoiceResponse](#multipleChoiceResponse), [MultipleResponseResponse](#multipleResponseResponse), [Organization](#organization), [Page](#page), [Person](#person), [Reading](#reading), [Response](#response), [Result](#result), [SelectTextResponse](#selectTextResponse), [Session](#session), [SharedAnnotation](#sharedAnnotation), [SoftwareApplication](#softwareapplication), [TagAnnotation](#tagAnnotation), [Thread](#thread), [TrueFalseResponse](#trueFalseResponse), [VideoObject](#videoobject), [WebPage](#webpage)

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/buildings/55/rooms/3027",
    "@type": "http://purl.imsglobal.org/caliper/v1/Entity",
    "name": "Rm 3027 Computer lab"
}
```

<a name="api"/>
## 8.0 Sensor API

TODO: OVERVIEW

<a name="transport"/>
## 9.0 Transport

TODO: OVERVIEW

<a name="endpoints"/>
### 9.1 Envelope

TODO: OVERVIEW

<a name="endpoints"/>
### 9.2 Endpoint

TODO: OVERVIEW

<a name="contributors"/>
## 10.0 Contributors
The following Caliper Working Group participants contributed to the writing of this specification:

| Name | Organization |
| ------ | --------- |
| Anthony Whyte | University of Michigan |
| Viktor Haag | D2L |
| Wes LaMarche | ACT |


<a name="appendixEvents"/>
## Appendix A. Caliper Events

<a name="annotationEvent" />
### AnnotationEvent
The AnnotationEvent models . . . .  AnnotationEvent inherits all the properties and requirements defined for Event, its superclass.  

#### TODO
* Add additional intro text
* Confirm: removal of actions

#### Supported actions
 [bookmarked](#bookmarked), [highlighted](#highlighted), [shared](#shared), [tagged](#tagged)
 
#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssessmentEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this AnnotationEvent. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged |
| object | [DigitalResource](#digitalResource) | DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | [Annotation](#annotation) | The Annotation SHOULD be specified.  Note that Annotation is a generic type that is subclassed for greater type specificity.  Utilize Annotation only if no suitable subclass exists to represent the object. |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.  |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: AnnotationEvent bookmarked
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/AnnotationEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Bookmarked",
  "object": {
    "@id": "https://example.edu/etexts/201.epub",
    "@type": "http://purl.imsglobal.org/caliper/v1/Document",
    "name": "IMS Caliper Implementation Guide",
    "version": "1.1"
  },
  "generated": {
    "@id": "https://example.edu/users/554433/etexts/201/bookmarks/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/BookmarkAnnotation",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "annotated": {
      "@id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!/4[body01]/10[para05]/1:20)",
      "@type": "http://purl.imsglobal.org/caliper/v1/Chapter"
    },
    "bookmarkNotes": "Caliper profiles model discrete learning activities or supporting activities that enable learning.",
    "dateCreated": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "name": "ePub Reader",
    "version": "1.2.3"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```
	
<a name="assessmentEvent" />
### AssessmentEvent
The AssessmentEvent models learner interactions with assessments instruments such as online tests or quizzes.  AssessmentEvent inherits all the properties and requirements defined for Event, its superclass.  

#### Supported actions
[started](#started), [paused](#paused), [restarted](#restarted), [submitted](#submitted)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssessmentEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this AssessmentEvent. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Started |
| object |  [Assessment](#assessment) , [Attempt](#attempt) | For [started](#started), [paused](#paused) and [restarted](#restarted) actions the Assessment is the REQUIRED object of the interaction; for a [submitted](#submitted) action the learner's [Attempt](#attempt) of the Assessment is the REQUIRED object.  When the Attempt is the object it MUST reference both the actor and the assigned Assessment.  A [count](#count) of the number of times the actor has interacted with the Assessment MUST also be specified.  The Attempt MAY also reference a parent Attempt via the [isPartOf](#isPartOf) property. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | [Attempt](#attempt) | The learner's Attempt SHOULD be specified in order to record a [count](#count) of the number of times the actor has interacted with the Assessment.  If an Attempt is included, both the actor and the assigned Assessment must be referenced. |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.  |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event.  | 

#### Example: AssessmentEvent started
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Started",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
    "name": "Quiz One",
    "dateToStartOn": "2016-11-14T05:00:00.000Z",
    "dateToSubmit": "2016-11-18T11:59:59.000Z",
    "maxAttempts": 2,
    "maxSubmits": 2,
    "maxScore": 25,
    "version": "1.0"
  },
  "generated": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
    },
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:15:00.000Z",
    "startedAtTime": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

#### Example: AssessmentEvent submitted
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Submitted",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
      "name": "Quiz One",
      "dateToStartOn": "2016-11-14T05:00:00.000Z",
      "dateToSubmit": "2016-11-18T11:59:59.000Z",
      "maxAttempts": 2,
      "maxSubmits": 2,
      "maxScore": 25,
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
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

<a name="assessmentItemEvent" />
### AssessmentItemEvent
The AssessmentItemEvent models a learner's interaction with an individual assessment item.  AssessmentItemEvent inherits all the properties and requirements defined for Event, its superclass.  

#### Supported actions
[started](#started), [skipped], [completed](#completed)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssessmentItemEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this AssessmentItemEvent. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Completed |
| object |   [AssessmentItem](#assessmentItem) , [Attempt](#attempt) | For [started](#started) and [skipped](#skipped) actions the AssessmentItem is the REQUIRED object of the interaction; for a [completed](#completed) action the learner's [Attempt](#attempt) of the AssessmentItem is the REQUIRED object.  When the Attempt is the object it MUST reference both the actor and the assigned AssessmentItem.  A [count](#count) of the number of times the actor has interacted with the AssessmentItem MUST also be specified.  The Attempt MAY also reference a parent Assessment Attempt via the [isPartOf](#isPartOf) property. |
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | [Attempt](#attempt), [Response](#response) | For [started](#started) and [skipped] actions, the learner's Attempt SHOULD be specified in order to record a [count](#count) of the number of times the actor has interacted with the AssessmentItem.  If the Attempt is provided it MUST reference both the actor and the assigned AssessmentItem. The Attempt MAY also reference a parent Attempt via the [isPartOf](#isPartOf) property.  For a [completed](#completed) action a generated Response MAY be referenced.  Note that Response is a generic type that is subclassed for greater type specificity.  Utilize Response only if no suitable subclass exists to represent the learner's response to the item. |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.  |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: AssessmentItem started
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItemEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Started",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
    "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
    "name": "Assessment Item 3",
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
    },
    "dateToStartOn": "2016-11-14T05:00:00.000Z",
    "dateToSubmit": "2016-11-18T11:59:59.000Z",
    "maxAttempts": 2,
    "maxSubmits": 2,
    "maxScore": 1,
    "isTimeDependent": false,
    "version": "1.0"
    },
  "generated": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem"
    },
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Attempt"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:15:00.000Z",
    "startedAtTime": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

#### Example: AssessmentItem completed
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItemEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Completed",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
      "name": "Assessment Item 3",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
      }
    },
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Attempt"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:15:02.000Z",
    "startedAtTime": "2016-11-15T10:15:02.000Z",
    "endedAtTime": "2016-11-15T10:15:12.000Z"
  },
  "generated": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/responses/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
    "attempt": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Attempt"
    },
    "dateCreated": "2016-11-15T10:15:12.000Z",
    "startedAtTime": "2016-11-15T10:15:02.000Z",
    "endedAtTime": "2016-11-15T10:15:12.000Z",
    "values": [ "subject", "object", "predicate" ]
  },
  "eventTime": "2016-11-15T10:15:12.000Z",
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

<a name="assignableEvent" />
### AssignableEvent
The AssignableEvent models . . . .  AssignableEvent inherits all the properties and requirements defined for Event, its superclass.  

TODO add additional intro text

#### Supported actions
[activated](#activated), [deactivated](#deactivated), [started](#started), [completed](#completed)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssignableEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this AssignableEvent.  |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Activated |
| object | [AssignableDigitalResource](#assignableDigitalResource) | AssignableDigitalResource is a generic type that is subclassed for greater type specificity.  Utilize AssignableDigitalResource only if no suitable subclass exists to represent the object. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | &nbsp; | &nbsp;  |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.  |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: AssignableEvent activated
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssignableEvent",
  "actor": {
    "@id": "https://example.edu/users/112233",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Activated",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
    "name": "Quiz One",
    "dateCreated": "2016-08-01T06:00:00.000Z",
    "dateModified": "2016-09-02T11:30:00.000Z",
    "datePublished": "2016-11-12T10:10:00.000Z",
    "dateToActivate": "2016-11-12T10:15:00.000Z",
    "dateToStartOn": "2016-11-14T05:00:00.000Z",
    "dateToSubmit": "2016-11-18T11:59:59.000Z",
    "maxAttempts": 2,
    "maxSubmits": 2,
    "maxScore": 25,
    "version": "1.0"
  },
  "eventTime": "2016-11-12T10:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/112233",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Instructor" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/f095bbd391ea4a5dd639724a40b606e98a631823",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-12T10:00:00.000Z"
  }
}
```

<a name="forumEvent" />
### ForumEvent

The ForumEvent models . . . .  ForumEvent inherits all the properties and requirements defined for Event, its superclass.

TODO add description

#### Supported actions
[subscribed](#subscribed), [unsubscribed](#unsubscribed)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/ForumEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this ForumEvent.  |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed |
| object | [Forum](#forum) | &nbsp;  | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | &nbsp; | &nbsp;  |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: ForumEvent subscribed
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/ForumEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
    "name": "Caliper Forum",
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "dateCreated": "2016-09-14T11:00:00.000Z"
  },
  "eventTime": "2016-11-15T10:16:00.000Z",
  "edApp": {
    "@id": "https://example.edu/forums",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

<a name="mediaEvent" />
### MediaEvent
A Caliper MediaEvent models . . . .  MediaEvent inherits all the properties and requirements defined for Event, its superclass.

TODO 
* add additional description.  
* Should MediaLocation be the object or the target of the interaction?
* Should ImageObject be included in this event (ViewEvent appears more appropriate)?

#### Supported actions
[started](#started), [paused](#paused), [resumed](#resumed), [forwardedTo](#forwardedTo), [jumpedTo](#jumpedTo), [rewound](#rewound), [ended](#ended), [changedResolution](#changedResolution), [changedSize](#changedSize), [changedSpeed](#changedSpeed), [changedVolume](#changedVolume), [enabledClosedCaptioning](#enabledClosedCaptioning), [disabledClosedCaptioning](#disabledClosedCaptioning), [enteredFullScreen](#enteredFullScreen), [exitedFullScreen](#exitedFullScreen), [muted](#muted), [unmuted](#unmuted), [openedPopout](#openedPopout), [closedPopout](#closedPopout)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MediaEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this MediaEvent.  |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Paused |
| object | [MediaObject](#mediaObject) | MediaObject is a generic type that is subclassed for greater type specificity.  Utilize MediaObject only if no suitable subclass exists to represent the object. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | [MediaLocation](#mediaLocation) | The MediaLocation [currentTime](#currentTime) property SHOULD be specified to provide a precise position in the audio or video stream that marks the action.  The value MUST be an ISO 8601 formatted duration, e.g., "PT30M54S". |
| generated | &nbsp;  | &nbsp; |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: MediaEvent paused
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/MediaEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Paused",
  "object": {
    "@id": "https://example.edu/UQVK-dsU7-Y",
    "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
    "name": "Information and Welcome",
    "mediaType": "video/ogg",
    "duration": "PT20M20S"
  },
  "target": {
    "@id": "https://example.edu/UQVK-dsU7-Y?t=321",
    "@type": "http://purl.imsglobal.org/caliper/v1/MediaLocation",
    "currentTime": "PT05M21S"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu/player",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

<a name="messageEvent" />
### MessageEvent
A Caliper [MessageEvent](#messageEvent) describes an [Person](#person) posting a [Message](#message) or marking a post as either read or unread.  MessageEvent inherits all the properties and requirements defined for Event, its superclass.

#### Supported actions
[posted](#posted), [markedAsRead](#markedAsRead), [markedAsUnRead](#markedAsUnRead)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MessageEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this MessageEvent. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Posted |
| object | [Message](#Message) | If the object represents a Message posted in reply to a previous message, the prior message  prompting the post SHOULD be referenced utilizing the Message [replyTo](#replyTo) property.  | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | &nbsp; | &nbsp; |
| referrer | [Entity](#entity) |  A referrer SHOULD be provided.  A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: MessageEvent posted
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/MessageEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Posted",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/2",
    "@type": "http://purl.imsglobal.org/caliper/v1/Message",
    "creators": [
      {
        "@id": "https://example.edu/users/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
      }
    ],
    "body": "Are the Caliper Sensor reference implementations production-ready?",
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "name": "Caliper Adoption",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2",
        "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
        "name": "Caliper Forum"
      }
    },
    "dateCreated": "2016-11-15T10:15:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu/forums",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

#### Example: MessageEvent posted (reply)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/MessageEvent",
  "actor": {
    "@id": "https://example.edu/users/778899",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Posted",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/3",
    "@type": "http://purl.imsglobal.org/caliper/v1/Message",
    "creators": [
      {
        "@id": "https://example.edu/users/778899",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
      }
    ],
    "replyTo": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/Message"
    },
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2",
        "@type": "http://purl.imsglobal.org/caliper/v1/Forum"
      }
    },
    "dateCreated": "2016-11-15T10:15:30.000Z"
  },
  "eventTime": "2016-11-15T10:15:30.000Z",
  "edApp": {
    "@id": "https://example.edu/forums",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/778899",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1d6fa9adf16f4892650e4305f6cf16610905cd50",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:12:00.000Z"
  }
}
```

<a name="navigationEvent" />
### NavigationEvent
The NavigationEvent models an actor traversing a network of digital resources.  NavigationEvent inherits all the properties and requirements defined for Event, its superclass.

#### Supported actions
[navigatedTo](#navigatedTo)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/NavigationEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this NavigationEvent. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo |
| object | [DigitalResource](#digitalResource) | DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | &nbsp; | &nbsp; |
| referrer | [Entity](#entity) |  The referrer SHOULD be provided.  A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: NavigationEvent navigated to
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/NavigationEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/pages/2",
    "@type": "http://purl.imsglobal.org/caliper/v1/WebPage",
    "name": "Learning Analytics Specifications",
    "description": "Overview of Learning Analytics Specifications with particular emphasis on IMS Caliper.",
    "dateCreated": "2016-08-01T09:00:00.000Z"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "referrer": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/pages/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/WebPage"
  },
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

<a name="outcomeEvent" />
### OutcomeEvent
The OutcomeEvent models . . . .  OutcomeEvent inherits all the properties and requirements defined for Event, its superclass.

TODO add description

#### Supported actions
[graded](#graded)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/OutcomeEvent |
| actor  | [Agent](#agent) | The Agent who initiated or is the subject of this OutcomeEvent.  For automated grading a [SoftwareApplication](#softwareApplication) SHOULD be specified as the actor.  For manual grading a [Person](#person) SHOULD be specified as the actor.  Note that Agent is a generic type that is subclassed for greater type specificity.  Utilize Agent only if no suitable subclass exists to represent the actor. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Graded |
| object | [Attempt](#attempt) | The Attempt [actor](#actor), [assignable](#assignable) and [count](#count) properties MUST be specified.  The Attempt [startedAtTime](#startedAtTime), [endedAtTime](#endedAtTime) and [duration](#duration) properties SHOULD be specified.  | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | [Result](#result) | A generated Result SHOULD be provided.  |
| referrer | [Entity](#entity) |  A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: OutcomeEvent graded
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/OutcomeEvent",
  "actor": {
    "@id": "https://example.edu/autograder",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Graded",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
    },
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "count": 1,
    "dateCreated": "2016-11-15T10:05:00.000Z",
    "startedAtTime": "2016-11-15T10:05:00.000Z",
    "endedAtTime": "2016-11-15T10:55:12.000Z",
    "duration": "PT50M12S"
  },
  "eventTime": "2016-11-15T10:57:06.000Z",
  "generated": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/results/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Result",
    "attempt": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Attempt"
    },
    "normalScore": 15,
    "totalScore": 15,
    "scoredBy": {
      "@id": "https://example.edu/autograder",
      "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
    },
    "dateCreated": "2016-11-15T10:55:05.000Z"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  }
}
```

<a name="sessionEvent" />
### SessionEvent
A SessionEvent models . . . .  SessionEvent inherits all the properties and requirements defined for Event, its superclass.

TODO add description

#### Supported actions
[loggedIn](#loggedIn), [loggedOut](#loggedOut), [timedOut](#timedOut)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SessionEvent |
| actor  | [Agent](#person) | The Agent who initiated or is the subject of this SessionEvent.  For [loggedIn](#loggedIn) and [loggedOut](#loggedOut) actions a [Person](#person) SHOULD be specified as the actor.  For a [timedOut](#timedOut) action a [SoftwareApplication](#softwareApplication) SHOULD be specified as the actor.  Note that Agent is a generic type that is subclassed for greater type specificity.  Utilize Agent only if no suitable subclass exists to represent the actor. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn |
| object | [Entity](#entity) | For [loggedIn](#loggedIn) and [loggedOut](#loggedOut) actions a [SoftwareApplication](#softwareApplication) SHOULD be specified as the object.  For a [timedOut](#timedOut) action the [Session](#session) SHOULD be specified as the object.  | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | [DigitalResource](#digitalResource) | &nbsp;  |
| generated | &nbsp; | &nbsp;  |
| referrer | [Entity](#entity) |  A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session) | For all actions supported, the Session [startedAtTime](#startedAtTime) SHOULD be specified.  For a [loggedIn](#loggedIn) action, the Session [endedAtTime](#endedAtTime) and [duration](#duration) MUST NOT be specified.  It is RECOMMENDED that a Session [endedAtTime](#endedAtTime) and [duration](#duration) be provided for [loggedOut](#loggedOut) and [timedOut](#timedOut) actions. | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: SessionEvent logged in
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "id": "341db3d9-71cc-4081-9423-cbed73cb0179",
  "@type": "http://purl.imsglobal.org/caliper/v1/SessionEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn",
  "object": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "dateCreated": "2016-11-15T10:00:00.000Z",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

#### Example: SessionEvent logged out
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "id": "5fac90a9-531a-41f6-9b8d-7a26e61dcc27",
  "@type": "http://purl.imsglobal.org/caliper/v1/SessionEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut",
  "object": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "eventTime": "2016-11-15T11:05:00.000Z",
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "dateCreated": "2016-11-15T10:00:00.000Z",
    "startedAtTime": "2016-11-15T10:00:00.000Z",
    "endedAtTime": "2016-11-15T11:05:00.000Z",
    "duration": "PT3000S"
  }
}
```

#### Example: SessionEvent timed out
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "id": "513d4ca1-0ecf-4234-932d-c4cb287884a3",
  "@type": "http://purl.imsglobal.org/caliper/v1/SessionEvent",
  "actor": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut",
  "object": {
    "@id": "https://example.edu/sessions/7d6b88adf746f0692e2e873308b78c60fb13a864",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "actor": {
      "@id": "https://example.edu/users/112233",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "dateCreated": "2016-11-15T10:15:00.000Z",
    "startedAtTime": "2016-11-15T10:15:00.000Z",
    "endedAtTime": "2016-11-15T11:15:00.000Z",
    "duration": "PT3600S"
  },
  "eventTime": "2016-11-15T11:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
  }
}
```

<a name="threadEvent" />
### ThreadEvent
A Caliper ThreadEvent models an actor marking a forum thread as either read or unread.  ThreadEvent inherits all the properties and requirements defined for Event, its superclass.

TODO add description

#### Supported actions
[markedAsRead](#markedAsRead), [markedAsUnRead](#markedAsUnread)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/ThreadEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this ThreadEvent.   |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead |
| object | [Thread](#thread) | &nbsp;  | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | &nbsp; | &nbsp;  |
| referrer | [Entity](#entity) |  A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example: ThreadEvent marked as read
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/ThreadEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead",
  "object": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
    "name": "Caliper Information Model",
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
      "name": "Caliper Forum",
      "dateCreated": "2016-11-15T10:15:00.000Z"
    },
    "dateCreated": "2016-11-15T10:16:00.000Z"
  },
  "eventTime": "2016-11-15T10:16:00.000Z",
  "edApp": {
    "@id": "https://example.edu/forums",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "version": "v2"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  }
}
```

<a name="viewEvent" />
### ViewEvent
A Caliper ViewEvent models an actor's examination of digital content whenever the activity emphasizes thoughtful observation or study as opposed to the mere retrieval of a file.   ViewEvent inherits all the properties and requirements defined for Event, its superclass.

#### Supported actions
[viewed](#viewed)

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/ViewEvent. |
| actor  | [Person](#person) | The Person who initiated or is the subject of this ViewEvent.   |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed |
| object | [DigitalResource](#digitalResource) | DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | [Frame](#frame) | &nbsp;  |
| generated | &nbsp; | &nbsp;  |
| referrer | [Entity](#entity) |  A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.   |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example ViewEvent viewed (with extensions)
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@type": "http://purl.imsglobal.org/caliper/v1/ViewEvent",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed",
  "object": {
    "@id": "https://example.edu/etexts/200.epub",
    "@type": "http://purl.imsglobal.org/caliper/v1/Document",
    "name": "IMS Caliper Specification",
    "version": "1.1"
  },
  "eventTime": "2016-11-15T10:15:00.000Z",
  "edApp": {
    "@id": "https://example.edu",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
  },
  "group": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  },
  "membership": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
    "member": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "organization": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    },
    "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
    "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "session": {
    "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
    "@type": "http://purl.imsglobal.org/caliper/v1/Session",
    "startedAtTime": "2016-11-15T10:00:00.000Z"
  },
  "extensions": {
    "@context": {
      "@vocab": "http://example.edu/ctx/edu.jsonld"
    },
    "job": {
      "@id": "https://example.edu/data/jobs/08c1233d-9ba3-40ac-952f-004c47a50ff7",
      "@type": "ChronJob",
      "jobTag": "caliper",
      "jobDate": "2016-11-16T01:01:00.000Z"
    }
  }
}
```

<a name="appendixEntities"/>
## Appendix B. Caliper Entities

<a name="agent" />
### Agent
A Caliper Agent is a generic class that represents an Entity that can initiate or perform an action.  It is analogous to a [foaf:Agent](http://xmlns.com/foaf/spec/#term_Agent).  Agent inherits all the properties and requirements defined for [Entity](#entity), its superclass.  Given that Agent represents a generic type it is RECOMMENDED that only subclasses of Agent be employed to represent nodes in the learning graph.

#### subClassOf
[Entity](#entity)

#### Subclasses 
[Organization](#organization), [Person](#person), [SoftwareApplication](#softwareapplication)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An Agent SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an Agent MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | If a generic Agent is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Agent; otherwise the value MUST be assigned the IRI appropriate for the subclass, e.g., http://purl.imsglobal.org/caliper/v1/Person. |

#### Optional properties
Inherited from [Entity](#entity).

<a name="annotation" />
### Annotation
A Caliper Annotation is a generic class that represents a comment, explanation, highlight, mark, note, question or tag linked to a [DigitalResource](#digitalResource).  The act of sharing a [DigitalResource](#digitalResource) with others is also considered a form of annotation.  Annotation inherits all the properties and requirements defined for [Entity](#entity), its superclass.  Given that Annotation represents a generic type it is RECOMMENDED that only subclasses of Annotation be employed to represent nodes in the learning graph.

#### subClassOf
[Entity](#entity)

#### Subclasses 
[BookmarkAnnotation](#bookmarkAnnotation), [HighlightAnnotation](#highlightAnnotation), [SharedAnnotation](#sharedAnnotation), [TagAnnotation](#tagAnnotation)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An Annotation SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an Annotation MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | If a generic Annotation is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Annotation; otherwise the value MUST be assigned the IRI appropriate for the subclass, e.g., http://purl.imsglobal.org/caliper/v1/BookmarkAnnotation. |
| actor | [Person](#person) | The Person who created the Annotation MUST be specified. |
| annotated | [DigitalResource](#digitalResource) | The DigitalResource that was annotated MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
Inherited from [Entity](#entity).

<a name="assessment" />
### Assessment
A Caliper Assessment represents TODO . . . .  Assessment inherits all the properties and requirements defined for both [AssignableDigitalResource](#assignableDigitalResource) and [Collection](#collection), its two superclasses.

#### subClassOf 
[AssignableDigitalResource](#assignableDigitalResource), [Collection](#collection)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An Assessment SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an Assessment MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Assessment. |

#### Optional properties
Inherited from [AssignableDigitalResource](#assignableDigitalResource) and [Collection](#collection).  Note that the Assessment [items](#items) property is an ordered list of type [AssessmentItem](#assessmentItem).

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| items | List&lt;[AssessmentItem](#assessmentItem)&gt; | The ordered set of items that comprise this Assessment. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
  "name": "Quiz One",
  "items": [
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem"
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem"
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem"
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
### AssessmentItem
A Caliper AssessmentItem represents TODO . . . .  Assessment inherits all the properties and requirements defined for [AssignableDigitalResource](#assignableDigitalResource), its superclass.

#### subClassOf 
[AssignableDigitalResource](#assignableDigitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An AssessmentItem SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an AssessmentItem MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssessmentItem. |

#### Optional properties
Inherited from [AssignableDigitalResource](#assignableDigitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
  "isPartOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
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
### AssignableDigitalResource
A Caliper AssignableDigitalResource is a generic class that represents digital content associated with a graded or ungraded assignment.  AssignableDigitalResource inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  Given that AssignableDigitalResource represents a generic type it is RECOMMENDED that only subclasses of AssignableDigitalResource be employed to represent nodes in the learning graph.

#### subClassOf
[DigitalResource](#digitalResource)

#### Subclasses 
[Assessment](#assessment), [AssessmentItem](#assessmentItem)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An AssignableDigitalResource SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an AssignableDigitalResource MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssignableDigitalResource. |

#### Optional properties
In addition to properties inherited from [DigitalResource](#digitalResource), AssignableDigitalResource includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| dateToActivate | [dateTime](#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision that represents when the assigned resource was activated. |
| dateToShow | [dateTime](#dateTime) |ISO 8601 formatted date and time expressed with millisecond precision that represents when the assigned resource should be shown or made available to learners. |
| dateToStartOn | [dateTime](#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision that represents when the assigned resource can be started. |
| maxAttempts | [nonNegativeInteger](#nonNegativeInteger)  | Non-negative integer representing the number of permitted attempts. |
| maxSubmits | [nonNegativeInteger](#nonNegativeInteger)  | Non-negative integer representing the number of permitted submissions. |
| maxScore | [nonNegativeInteger](#nonNegativeInteger)  | Non-negative integer representing the maximum score permitted. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assign/2",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssignableDigitalResource",
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
### Attempt
A Caliper Attempt provides a count of the number of times an actor has interacted with an [AssignableDigitalResource](#assignabledigitalresource) along with start time, end time and duration information.  An Attempt is generated as the result of an action such as starting an [Assessment](#assessment).  Attempt inherits all the properties and requirements defined for [Entity](#entity), its superclass. 

#### subClassOf 
[Entity](#entity)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An Attempt SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an Attempt MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Attempt. |
| actor | [Person](#person) | The Person who initiated the Attempt SHOULD be specified. |
| assignable | [DigitalResource](#digitalResource) | The DigitalResource that constitutes the object of the assignment SHOULD be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |
| count | [xsd:nonNegativeInteger](https://www.w3.org/TR/xmlschema11-2/#nonNegativeInteger) | The total number of attempts inclusive of the current Attempt that have been registered against the assigned DigitalResource. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Attempt includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| isPartOf | [Attempt](#attempt) | The parent Attempt of this Attempt MAY be specified. |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | Represents when this Attempt commenced.  A start time SHOULD be provided.  If a start time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | Represents when this Attempt ended or was terminated.  For a [completed](#completed) or [submitted](#submitted) action an end time SHOULD be provided.  If an end time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | Represents the total interval of time required to complete this Attempt.  If a duration is specified the value MUST conform to the ISO-8601 duration format. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
  "assignable": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
  },
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "count": 1,
  "dateCreated": "2016-11-15T10:05:00.000Z",
  "startedAtTime": "2016-11-15T10:05:00.000Z",
  "endedAtTime": "2016-11-15T10:55:30.000Z",
  "duration": "PT50M30S"
}
```

<a name="audioObject" />
### AudioObject
A Caliper AudioObject represents an audio or sound file.  AudioObject inherits all the properties and requirements defined for [MediaObject](#mediaObject), its superclass.  It is analogous to an [sdo:AudioObject](http://schema.org/AudioObject).

#### subClassOf 
[MediaObject](#mediaObject)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An AudioObject SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an AudioObject MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AudioObject. |

#### Optional properties
Inherited from [MediaObject](#mediaObject).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/audio/765",
  "@type": "http://purl.imsglobal.org/caliper/v1/AudioObject",
  "name": "Audio Recording: IMS Caliper Sensor API Q&A.",
  "mediaType": "audio/ogg",
  "datePublished": "2016-12-01T06:00:00.000Z",
  "duration": "PT55M13S"
}
```

<a name="bookmarkAnnotation" />
### BookmarkAnnotation
A Caliper BookmarkAnnotation represents the act of marking a [DigitalResource](#digitalResource) at a particular location.  BookmarkAnnotation inherits all the properties and requirements defined for [Annotation](#annotation), its superclass.

#### subClassOf
[Annotation](#annotation)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A BookmarkAnnotation SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a BookmarkAnnotation MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/BookmarkAnnotation. |
| actor | [Person](#person) | The Person who created the Annotation MUST be specified. |
| annotated | [DigitalResource](#digitalResource) | The DigitalResource that was annotated MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from Annotation](#annotation), BookmarkAnnotation includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| bookmarkNotes | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A comment or note that accompanies the bookmark. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/users/554433/etexts/201/bookmarks/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/BookmarkAnnotation",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "annotated": {
    "@id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!/4[body01]/10[para05]/1:20)",
    "@type": "http://purl.imsglobal.org/caliper/v1/Chapter"
  },
  "bookmarkNotes": "Caliper profiles model discrete learning activities or supporting activities that facilitate learning.",
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="chapter" />
### Chapter
A Caliper Chapter represents a major sub-division of a piece of digital content.  Document inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Chapter SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Chapter MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Chapter. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!)",
  "@type": "http://purl.imsglobal.org/caliper/v1/Chapter",
  "name": "The Caliper Information Model",
  "isPartOf": {
    "@id": "https://example.edu/etexts/201.epub",
    "@type": "http://purl.imsglobal.org/caliper/v1/Document",
    "dateCreated": "2016-10-01T06:00:00.000Z",
    "name": "IMS Caliper Implementation Guide",
    "version": "1.1"
  }
}
```

<a name="collection" />
### Collection
A Caliper Collection is a generic class that represents an ordered set of entities.  Collection inherits all the properties and requirements defined for [Entity](#entity), its superclass.  It also includes an optional [items](#items) property for referencing the ordered list of entities that comprise the Collection.  Given that Collection represents a generic type it is RECOMMENDED that only subclasses of Collection be employed to represent nodes in the learning graph.  Collection is analogous to a [dcmitype:Collection](http://purl.org/dc/dcmitype/Collection) or a [sioc:Container](http://rdfs.org/sioc/spec/#term_Container).

#### subClassOf
[Entity](#entity)

#### Subclasses 
[DigitalResourceCollection](#digitalResourceCollection)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Collection SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Collection MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Collection. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Collection includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| isPartOf | [Entity](#entity) | The parent Entity of this Collection. |
| items | List&lt;[Entity](#entity)&gt; | The ordered set of items that comprise this Collection. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/groups",
  "@type": "http://purl.imsglobal.org/caliper/v1/Collection",
  "name": "Groups",
  "items": [
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/groups/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Group"
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/groups/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/Group"
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/groups/5",
      "@type": "http://purl.imsglobal.org/caliper/v1/Group"
    }
  ],
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="courseOffering" />
### CourseOffering
A Caliper CourseOffering represents the occurrence of a course or a class in a specific semester, term or period.  CourseOffering is composed of a subset of properties specified in the IMS [LTI 2.0](#lti) specification, which in turn, draws inspiration from the IMS [LIS 1.0](#lis) specification.  CourseOffering inherits all the properties and requirements defined for [Organization](#organization), its superclass.

#### subClassOf
[Organization](#organization)

#### Subclasses 
[CourseSection](#courseSection)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A CourseOffering SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a CourseOffering MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/CourseOffering. |

#### Optional properties
In addition to properties inherited from [Organization](#organization), CourseOffering includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| courseNumber | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A short-hand identifer of this CourseOffering. |
| academicSession | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The designated period in which this CourseOffering occurs.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7",
  "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering",
  "courseNumber": "CPS 435",
  "academicSession": "Fall 2016",
  "name": "CPS 435 Learning Analytics",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="courseSection" />
### CourseSection
A Caliper CourseSection represents an instance of a [CourseOffering](#courseOffering) occuring during a specific semester, term or period.  A CourseSection may include sub-sections (each is created as a separate [Group](#group)).  CourseSection is composed of a subset of properties specified in the IMS [LTI 2.0](#lti) specification, which in turn, draws inspiration from the IMS [LIS 1.0](#lis) specification.  CourseSection inherits all the properties and requirements defined for [CourseOffering](#courseOffering), its superclass.

#### subClassOf
[CourseOffering](#courseOffering)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A CourseSection SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a CourseSection MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/CourseSection. |

#### Optional properties
In addition to properties inherited from [CourseOffering](#courseOffering), CourseSection includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| category | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | Label that characterizes the purpose of the section such as lecture, lab or seminar.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
  "academicSession": "Fall 2016",
  "courseNumber": "CPS 435-01",
  "name": "CPS 435 Learning Analytics, Section 01",
  "category": "seminar",
  "subOrganizationOf": {
    "@id": "https://example.edu/terms/201601/courses/7",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering",
    "courseNumber": "CPS 435"
  },
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="digitalResource" />
### DigitalResource
A Caliper DigitalResource is a generic class that represents a content item.  DigitalResource inherits all the properties and requirements defined for [Entity](#entity), its superclass.  Given that DigitalResource represents a generic type it is RECOMMENDED that only subclasses of DigitalResource be employed to represent nodes in the learning graph.  It is analogous to an [sdo:CreativeWork](https://schema.org/CreativeWork).

TODO
* confirm: change property name alignedLearningObjective to learningObjectives to match naming pattern of other properties.

#### subClassOf 
[Entity](#entity)

#### Subclasses
[AssignableDigitalResource](#assignableDigitalResource), [Chapter](#chapter), [DigitalResourceCollection](#digitalResourceCollection), [Document](#document), [Forum](#forum), [Frame](#frame), [MediaLocation](#mediaLocation), [MediaObject](#mediaobject), [Message](#message), [Page](#page), [Thread](#thread), [WebPage](#webpage)

#### Deprecated subclasses
[EpubChapter](#epubChapter), [EpubPart](#epubPart), [EpubSubChapter](#epubSubChapter), [EpubVolume](#epubVolume), [Reading](#reading)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A DigitalResource SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a DigitalResource MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) |  If a generic DigitalResource is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/DigitalResource; otherwise the value MUST be assigned the IRI appropriate for the subclass, e.g., http://purl.imsglobal.org/caliper/v1/Message.  |

#### Optional properties
In addition to properties inherited from [Entity](#entity), DigitalResource includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| creators | List&lt;[Agent](#agent)&gt; | An ordered list of agents, typically of type Person, responsible for bringing this DigitalResource into being.  Analogous to [sdo:Creator](http://schema.org/Creator) or [dcterms:creator](http://purl.org/dc/terms/creator). |
| mediaType | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) | TODO |
| keywords | List&lt;[xsd:string](https://www.w3.org/TR/xmlschema11-2/#string)&gt; | A set of one or more words or expressions that are used to identify this DigitalResource.  Analogous to [sdo:keywords](http://schema.org/keywords) |
| learningObjectives | List&lt;[LearningObjective](#learningobjective)&gt; | One or more [LearningObjectives](#learningobject) that describe what the actor is expected to accomplish after engaging with this DigitalResource. |
| isPartOf | [Entity](#entity) | A related Entity, typically a DigitalResource, that includes or incorporates this DigitalResource as a part of its whole.  Analogous to [sdo:isPartOf](http://schema.org/isPartOf) or [dcterms:isPartOf](http://purl.org/dc/terms/isPartOf). |
| datePublished | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | Represents the publication date of this DigitalResource.  If a publication date is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [sdo:datePublished](http://schema.org/datePublished) |
| version | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) | An identifier that designates the current form of this DigitalResource.  Analogous to [sdo:version](http://schema.org/version) |

#### Deprecated properties
The following properties have been deprecated and will be removed in a future version of the specification.  Deprecated properties SHOULD NOT be referenced.

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| objectType | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) |  DEPRECATED |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/resources/1/syllabus.pdf",
  "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResource",
  "name": "Course Syllabus",
  "mediaType": "application/pdf",
  "creators": [
    {
      "@id": "https://example.edu/users/223344",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    }
  ],
  "isPartOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/resources/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResourceCollection",
    "name": "Course Assets",
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
    }
  },
  "dateCreated": "2016-08-02T11:32:00.000Z"
}
```

<a name="digitalResourceCollection" />
### DigitalResourceCollection
A Caliper DigitalResourceCollection is a generic class that represents an ordered set of digital content.  DigitalResourceCollection inherits all the properties and requirements defined for [Collection](#collection) and [DigitalResource](#digitalResources), its superclasses.

#### subClassOf
[Collection](#collection)

#### Subclasses 
[Assessment](#assessment), [Forum](#forum), [Thread](#thread)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A DigitalResourceCollection SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a DigitalResourceCollection MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Collection. |

#### Optional properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| isPartOf | [Entity](#entity) | The parent Entity of this Collection. |
| items | List&lt;[DigitalResource](#digitalResource)&gt; | The ordered set of items that comprise this Collection. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/resources/2",
  "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResourceCollection",
  "name": "Video Collection",
  "keywords": ["collection", "videos"],
  "items": [
    {
      "@id": "https://example.edu/videos/1225",
      "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
      "mediaType": "video/ogg",
      "name": "Introduction to IMS Caliper",
      "dateCreated": "2016-08-01T06:00:00.000Z",
      "duration": "PT1H12M27S",
      "version": "1.1"
    },
    {
      "@id": "https://example.edu/videos/5629",
      "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
      "mediaType": "video/ogg",
      "name": "IMS Caliper Activity Profiles",
      "dateCreated": "2016-08-01T06:00:00.000Z",
      "duration": "PT55M13S",
      "version": "1.1.1"
    }
  ],
  "isPartOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "subOrganizationOf": {
      "@id": "https://example.edu/terms/201601/courses/7",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering"
    }
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="document" />
### Document
A Caliper Document represents a piece of digital content.  Document inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Document SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Document MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Document. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/etexts/201.epub",
  "@type": "http://purl.imsglobal.org/caliper/v1/Document",
  "name": "IMS Caliper Implementation Guide",
  "mediaType": "application/epub+zip",
  "creators": [
    {
      "@id": "https://example.edu/people/12345",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    {
      "@id": "https://example.com/staff/56789",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    }
  ],
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "datePublished": "2016-10-01T06:00:00.000Z",
  "version": "1.1"
}
```
 
<a name="epubChapter" />
### EpubChapter (DEPRECATED)
A Caliper EpubChapter represents a major structural division of a piece of writing.  EpubChapter inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  It is analogous to an [idpf:chapter](http://www.idpf.org/epub/vocab/structure/#chapter).  EpubChapter is a deprecated entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An EpubChapter SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an EpubChapter MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/EpubChapter. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

<a name="epubPart" />
### EpubPart (DEPRECATED)
A Caliper EpubPart represents a major structural division of a piece of writing, typically encapsulating a set of related chapters.  EpubPart inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  It is analogous to an [idpf:part](http://www.idpf.org/epub/vocab/structure/#part).  EpubChapter is a deprecated entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An EpubPart SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an EpubPart MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/EpubPart. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

<a name="epubSubChapter" />
### EpubSubChapter (DEPRECATED)
A Caliper EpubSubChapter represents a major sub-division of an [EpubChapter](#EpubChapter).  EpubSubChapter inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  It is analogous to an [idpf:subchapter](http://www.idpf.org/epub/vocab/structure/#subchapter).  EpubSubChapter is a deprecated entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An EpubSubChapter SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an EpubSubChapter MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/EpubSubChapter. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

<a name="epubVolume" />
### EpubVolume (DEPRECATED)
A Caliper EpubVolume represents a component of a collection.  EpubVolume inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  It is analogous to an [idpf:volume](http://www.idpf.org/epub/vocab/structure/#volume).  EpubVolume is a deprecated entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An EpubVolume SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an EpubVolume MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/EpubSubChapter. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

<a name="fillinBlankResponse" />
### FillinBlankResponse
A Caliper FillinBlankResponse represents a form of response in which a respondent is asked to provide one or more words, expressions or short phrases that correctly completes a statement.  FillinBlankResponse inherits all the properties and requirements defined for [Response](#response), its superclass.

#### TODO
* confirm: eliminate actor and assignable in favor of attempt in order to eliminate unnecessary redundancy.

#### subClassOf 
[Response](#response)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A FillinBlankResponse SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a FillinBlankResponse MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/FillinBlankResponse. |
| attempt | [Attempt](#attempt) | The associated Attempt MUST be specified.  The Attempt MUST reference both the Person who initiated the Response and the DigitalResource that constitutes the object of the assignment.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Response](#response), FillinBlankResponse includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| value | List&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt; | The ordered set of one or more words, expressions or short phrases that constitutes the response MAY be provided.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1/users/554433/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
  "attempt": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
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
### Forum
A Caliper Forum represents a channel or virtual space in which group discussions take place.  A Forum typically comprises one or more threaded discussions to which members can subscribe, post messages and reply to other messages.  Frame inherits all the properties and requirements defined for [DigitalResourceCollection](#digitalResourceCollection), its superclass.  It is analogous to a [sioc:Forum](http://rfds.org/sioc/spec/#term_Forum).

#### subClassOf 
[DigitalResourceCollection](#digitalResourceCollection)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Forum SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Forum MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Forum. |

#### Optional properties
Inherited from [DigitalResourceCollection](#digitalResourceCollection).

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| items | List&lt;[Thread](#thread)&gt; | The ordered set of threaded discussions that comprise this Forum. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
  "name": "Caliper Forum",
  "items": [
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "name": "Caliper Information Model",
      "dateCreated": "2016-11-01T09:30:00.000Z"
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "name": "Caliper Sensor API",
      "dateCreated": "2016-11-01T09:30:00.000Z"
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "name": "Caliper Certification",
      "dateCreated": "2016-11-01T09:30:00.000Z"
    }
  ],
  "isPartOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "subOrganizationOf": {
      "@id": "https://example.edu/terms/201601/courses/7",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering"
    }
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="frame" />
### Frame
A Caliper Frame represents TODO . . . .  Frame inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Frame SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Frame MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Frame. |
| index | nonNegativeInteger | The character position TODO . . . . |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/etexts/201?index=2502",
  "@type": "http://purl.imsglobal.org/caliper/v1/Frame",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "index": 2502,
  "isPartOf": {
    "@id": "https://example.edu/etexts/201",
    "@type": "http://purl.imsglobal.org/caliper/v1/Document",
    "name": "IMS Caliper Implementation Guide",
    "version": "1.1"
  }
} 
```

<a name="group" />
### Group
A Caliper Group represents a sub-section of a [CourseSection](#courseSection) organized for some educational or social purpose.  The Group can act as an [Agent] and can often be decomposed into sub-groupings.  Group inherits all the properties and requirements defined for [Organization](#organization), its superclass.  It is analogous to an IMS LIS Group.

### TODO
Should we rename Group to LisGroup or CourseSectionGroup (and save Group for a more generic role)?

#### subClassOf
[Organization](#organization)

### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Group SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Group MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Group. |

#### Optional properties
Inherited from [Organization](#organization).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/groups/2",
  "@type": "http://purl.imsglobal.org/caliper/v1/Group",
  "name": "Discussion Group 2",
  "subOrganizationOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "subOrganizationOf": {
      "@id": "https://example.edu/terms/201601/courses/7",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering"
    }
  },
  "dateCreated": "2016-11-01T06:00:00.000Z"
}
```

<a name="highlightAnnotation" />
### HighlightAnnotation
A Caliper HighlightAnnotation represents the act of marking a particular segment of a  DigitalResource between two known points.  HighlightAnnotation inherits all the properties and requirements defined for [Annotation](#annotation), its superclass.

### TODO
* Add additional instructions regarding start and end properties

#### subClassOf
[Annotation](#annotation)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A HighlightAnnotation SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a HighlightAnnotation MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/HighlightAnnotation. |
| actor | [Person](#person) | The Person who created the Annotation MUST be specified. |
| annotated | [DigitalResource](#digitalResource) | The DigitalResource that was annotated MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from Annotation](#annotation), HighlightAnnotation includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| selection | [TextPositionSelector](#textPositionSelector) | The range of highlighted text based on its  [start](#start) and [end](#end) positions.  If the hightlighted selection is specified, both the [start](#start) and [end](#end) properties MUST be specified. |
| selectionText | The highlighted segment of the annotated DigitalResource. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/users/554433/etexts/201/highlights/20",
  "@type": "http://purl.imsglobal.org/caliper/v1/HighlightAnnotation",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "annotated": {
    "@id": "https://example.edu/etexts/201",
    "@type": "http://purl.imsglobal.org/caliper/v1/Document"
  },
  "selection": {
    "start": 2300,
    "end": 2370
  },
  "selectionText": "ISO 8601 formatted date and time expressed with millisecond precision.",
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="imageObject" />
### ImageObject
A Caliper ImageObject represents an image file.  ImageObject inherits all the properties and requirements defined for [MediaObject](#mediaObject), its superclass.  It is analogous to [sdo:ImageObject](http://schema.org/ImageObject).

#### subClassOf 
[MediaObject](#mediaObject)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An ImageObject SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an ImageObject MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/ImageObject. |

#### Optional properties
Inherited from [MediaObject](#mediaObject).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/images/caliper_lti.jpg",
  "@type": "http://purl.imsglobal.org/caliper/v1/ImageObject",
  "name": "IMS Caliper/LTI Integration Work Flow",
  "mediaType": "image/jpeg",
  "dateCreated": "2016-09-01T06:00:00.000Z"
}
```

<a name="learningObjective" />
### LearningObjective
The Caliper LearningObjective represents a summary statement that outlines the learning-related goals that a learner is expected to attain as a result of engaging in a learning activity.  LearningObjective inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A LearningObjective SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a LearningObjective MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/LearningObjective. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assign/2",
  "@type": "http://purl.imsglobal.org/caliper/v1/AssignableDigitalResource",
  "name": "Caliper Profile Design",
  "description": "Choose a learning activity and describe the actions, entities and events that comprise it.",
  "learningObjectives": [
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/objectives/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/LearningObjective",
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
### LtiSession
A Caliper LtiSession represents an LTI Tool Consumer Web application user session.  LtiSession inherits all the properties and requirements defined for [Session](#session), its superclass. 

#### subClassOf
[Session](#session)

#### Required properties
| Property | Type | Requirements |
| -------- | ---- | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An LtiSession SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an LtiSession MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/LtiSession. |

#### Optional properties
In addition to properties inherited from [Session](#session), LtiSession includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| launchParameters | Object | LTI-specified launch parameters that provide Tool Consumer-related contextual information.  LTI parameters of whatever type (i.e., required, recommended, optional, custom and extension) included in the launch request message MAY be referenced.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/sessions/b533eb02823f31024e6b7f53436c42fb99b31241",
  "@type": "http://purl.imsglobal.org/caliper/v1/LtiSession",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
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
      "@type": "Faculty",
      "sdo:jobTitle": "Professor",
      "sdo:givenName": "Trig",
      "sdo:familyName": "Haversine",
      "sdo:email": "trighaversine@example.edu",
      "sdo:url": "https://example.edu/faculty/trighaversine",
      "isTenured": true,
      "isOnSabbatical": false
    }
  },
  "dateCreated": "2016-11-15T10:15:00.000Z",
  "startedAtTime": "2016-11-15T10:15:00.000Z"
}
```

<a name="mediaLocation" />
#### MediaLocation

TODO

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/videos/1225",
  "@type": "http://purl.imsglobal.org/caliper/v1/MediaLocation",
  "currentTime": "PT30M54S",
  "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="mediaObject" />
### MediaObject
A Caliper MediaObject represents a generic piece of media content.  MediaObject inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  Given that MediaObject represents a generic type it is RECOMMENDED that only subclasses of DigitalResource be employed to represent nodes in the learning graph.  MediaObject is analogous to [sdo:MediaObject](http://schema.org/MediaObject).

#### TODO
confirm: Migrate MediaObject.duration to AudioObject and VideoObject (irrelevant property for ImageObject to inherit).

#### subClassOf 
[DigitalResource](#digitalResource)

#### Subclasses
[AudioObject](#audioObject.md), [ImageObject](#imageObject.md), [VideoObject](#videoObject)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A MediaObject SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a MediaObject MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | If a generic MediaObject is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MediaObject; otherwise the value MUST be assigned the IRI appropriate for the subclass, e.g., http://purl.imsglobal.org/caliper/v1/VideoObject.  |

#### Optional properties
In addition to properties inherited from [DigitalResource](#digitalResource), MediaObject includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | Represents the total interval of time required to complete this MediaObject.  If a duration is specified the value MUST conform to the ISO-8601 duration format. |

<a name="membership" />
### Membership
A Caliper Membership describes the relationship between an [Organization](#organization) and a [Person](#person) (i.e., a [member](#member)) in terms of the roles assigned and current status.  Membership inherits all the properties and requirements defined for [Entity](#entity), its superclass.

#### subClassOf 
[Entity](#entity)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Membership SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Membership MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Membership. |
| organization | [Organization](#organization) | The Organization associated with this Membership MUST be specified. |
| member | [Person](#person) ] | The Person who is the member of the associated Organization MUST be specified. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Membership includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| roles | List&lt;[Role](#role)&gt; | The organizational roles assigned to a member SHOULD be specified.  If a role is specified, the value MUST be chosen from the defined set of [roles](#roles]. |
| status | string | The member's current status SHOULD be specified.  If a status is specified, the value MUST be set to the one of the following defined states:  [active](#active], [deleted](#deleted) or [inactive](#inactive). |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/rosters/1/members/554433",
  "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
  "member": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "organization": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "subOrganizationOf": {
      "@id": "https://example.edu/terms/201601/courses/7",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering"
    }
  },
  "roles": [ "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner" ],
  "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
  "dateCreated": "2016-11-01T06:00:00.000Z"
}
```

<a name="message" />
### Message
A Caliper Message is a digital form of written communication sent to a recipient. A series of messages Messages may constitute a [Thread](#thread) if they share a common subject and are connected by a reply or by date relationships.  Message inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  It is analogous to an [sioc:Post](http://rfds.org/sioc/spec/#term_Post).

### TODO
* confirm if content property is to be excluded.
* confirm if attachments property is to be excluded.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Message SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Message MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Message.  |

#### Optional properties
In addition to properties inherited from [DigitalResource](#digitalResource), MediaObject includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| replyTo | [Message](#message) | If this Message represents a reply or a response to a previous Message, the Message prompting the reply SHOULD be referenced.  Analogous to [sioc:reply_of](http://rdfs.org/sioc/spec/#term_reply_of). |
| body | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) | Plain-text rendering of the body content of the Message.  Analogous to [sioc:content](http://rdfs.org/sioc/spec/#content). |
| attachments | List&lt;[DigitalResource](#digitalResource)&gt; | An ordered set of one or more items attached to this Message.  Analogous to [sioc:attachment](http://rdfs.org/sioc/spec/#term_attachment). |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/3",
  "@type": "http://purl.imsglobal.org/caliper/v1/Message",
  "creators": [
    {
      "@id": "https://example.edu/users/778899",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    }
  ],
  "body": "The Caliper working group provides a set of Caliper Sensor reference implementations for the purposes of education and experimentation.  They have not been tested for use in a production environment.  See the Caliper Implementation Guide for more details.",
  "replyTo": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1/messages/2",
    "@type": "http://purl.imsglobal.org/caliper/v1/Message"
  },
  "isPartOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2/topics/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/Forum"
    }
  },
  "attachments": [
    {
      "@id": "https://example.edu/etexts/201.epub",
      "@type": "http://purl.imsglobal.org/caliper/v1/Document",
      "name": "IMS Caliper Implementation Guide",
      "dateCreated": "2016-10-01T06:00:00.000Z",
      "version": "1.1"
    }
  ],
  "dateCreated": "2016-11-15T10:15:30.000Z"
}
 ```
 
<a name="multipleChoiceResponse" />
### MultipleChoiceResponse
A Caliper MultipleChoiceResponse represents a form of response in which a respondent is asked to provide the best possible answer from a list of choices.  MultipleChoiceResponse inherits all the properties and requirements defined for [Response](#response), its superclass.

#### TODO
* confirm: eliminate actor and assignable in favor of attempt in order to eliminate unnecessary redundancy.

#### subClassOf 
[Response](#response)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A MultipleChoiceResponse SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a MultipleChoiceResponse MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MultipleChoiceResponse. |
| attempt | [Attempt](#attempt) | The associated Attempt MUST be specified.  The Attempt MUST reference both the Person who initiated the Response and the DigitalResource that constitutes the object of the assignment.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Response](#response), MultipleChoiceResponse includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| value | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The selected option that constitutes the response MAY be provided.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2/users/554433/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/MultipleChoiceResponse",
  "attempt": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
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
### MultipleResponseResponse
A Caliper MultipleResponseResponse represents a form of response in which a respondent is asked to select more than one correct answer from a list of choices.  MultipleResponseResponse inherits all the properties and requirements defined for [Response](#response), its superclass.

#### subClassOf 
[Response](#response)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A MultipleResponseResponse SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a MultipleResponseResponse MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MultipleResponseResponse. |
| attempt | [Attempt](#attempt) | The associated Attempt MUST be specified.  The Attempt MUST reference both the Person who initiated the Response and the DigitalResource that constitutes the object of the assignment.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Response](#response), MultipleResponseResponse includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| values | List&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt; | The ordered set of one or more selected options that constitutes the response MAY be provided.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/MultipleResponseResponse",
  "attempt": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
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
### Organization
A Caliper Organization represents a group of people who come together for a common purpose, typically one that is educational, social or administrative in nature.  The Organization can act as an [Agent] and can often be decomposed into sub-organizations.  Organization inherits all the properties and requirements defined for [Agent](#agent), its superclass.  It is analogous to a [w3c:Organization](https://www.w3.org/TR/vocab-org/#class-organization).

#### subClassOf
[Agent](#agent)

#### Subclasses 
[CourseOffering](#CourseOffering), [CourseSection](#CourseSection), [Group](#group)

### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An Organization SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an Organization MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Organization. |

#### Optional properties
In addition to properties inherited from [Agent](#agent), Organization includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| subOrganizationOf| [Organization](#organization) | The parent Organization of this Organization MAY be specified if it provides additional useful contextual information. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/colleges/1/depts/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Organization",
  "name": "Computer Science Department",
  "subOrganizationOf": {
    "@id": "https://example.edu/colleges/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Organization",
    "name": "College of Engineering"
  }
}
```

<a name="page" />
### Page
A Caliper Page represents an item of paginated content.  Page inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Page SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Page MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Page. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/etexts/201/chs/2/pp/23",
  "@type": "http://purl.imsglobal.org/caliper/v1/Page",
  "name": "Page 23",
  "isPartOf": {
    "@id": "https://example.edu/etexts/201/chs/2",
    "@type": "http://purl.imsglobal.org/caliper/v1/Chapter",
    "name": "Chapter 2",
    "isPartOf": {
      "@id": "https://example.edu/etexts/201",
      "@type": "http://purl.imsglobal.org/caliper/v1/Document",
      "name": "IMS Caliper Implementation Guide",
      "dateCreated": "2016-10-01T06:00:00.000Z",
      "version": "1.1"
    }
  }
}
```

<a name="person" />
### Person
A Caliper Person represents a human being, alive or deceased, real or imaginary.  Person inherits all the properties and requirements defined for [Agent](#agent), its superclass.  It is analogous to a [foaf:Person](http://xmlns.com/foaf/spec/#term_Person).

#### subClassOf
[Agent](#agent)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Person SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Person MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Person. |

#### Optional properties
Inherited from [Agent](#agent).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/users/554433",
  "@type": "http://purl.imsglobal.org/caliper/v1/Person",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="reading" />
### Reading (DEPRECATED)
A Caliper Reading represents an item of paginated content.  Reading inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  Reading is a deprecated entity that will be removed in a future version of the specification.  It SHOULD NOT be referenced.

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Reading SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Reading MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Reading. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

<a name="response" />
### Response
A Caliper Response is a generic class that represents the selected option provided by a [Person](#person) interacting with an [AssessmentItem](#assessmentItem).  Given that Response represents a generic type it is RECOMMENDED that only subclasses of Response be employed to represent nodes in the learning graph. 

TODO
* confirm deprecating actor and assignable in favor of Attempt to eliminate redundancy.  Make Attempt required.

#### subClassOf 
[Entity](#entity)

#### Subclasses
[FillinBlankResponse](#fillinblankResponse.md), [MultipleChoiceResponse](#multipleChoiceResponse), [MutlipleResponseResponse](#mutlipleResponseResponse), [SelectTextResponse](#selectTextResponse), [TrueFalseResponse](#trueFalseResponse)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Response SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Response MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | If a generic Response is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Response; otherwise the value MUST be assigned the IRI appropriate for the subclass, e.g., http://purl.imsglobal.org/caliper/v1/TrueFalseResponse. |
| attempt | [Attempt](#attempt) | The associated Attempt MUST be specified.  The Attempt MUST reference both the Person who initiated the Response and the DigitalResource that constitutes the object of the assignment.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Response includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | Represents when this Response commenced.  A start time SHOULD be provided.  If a start time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | Represents when this Response was completed or ended.  An end time SHOULD be provided.  If an end time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) |Represents the total interval of time required to complete this Response.  If a duration is specified the value MUST conform to the ISO-8601 duration format. |

<a name="result" />
### Result

TODO

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1/results/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Result",
  "attempt": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
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
    "@id": "https://example.edu/autograder",
    "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
    "dateCreated": "2016-11-15T10:55:58.000Z"
  },
  "dateCreated": "2016-11-15T10:56:00.000Z"
}
```

<a name="selectTextResponse" />
### SelectTextResponse
A Caliper SelectTextResponse represents a response that identifies text or a mapping from a presented paragraph or list.  SelectTextResponse inherits all the properties and requirements defined for [Response](#response), its superclass.

#### subClassOf 
[Response](#response)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A SelectTextResponse SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a SelectTextResponse MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SelectTextResponse. |
| attempt | [Attempt](#attempt) | The associated Attempt MUST be specified.  The Attempt MUST reference both the Person who initiated the Response and the DigitalResource that constitutes the object of the assignment.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Response](#response), SelectTextResponse includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| values | List&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt; | The ordered set of one or more selected text options that constitutes the response MAY be provided.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/4/users/554433/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/SelectTextResponse",
  "attempt": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/4/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/4",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
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
### Session
A Caliper Session represents a Web application user session.  Session inherits all the properties and requirements defined for [Entity](#entity), its superclass. 

#### subClassOf
[Entity](#entity)

#### subclasses
[LtiSession](#ltiSession)

#### Required properties
| Property | Type | Requirements |
| -------- | ---- | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Session SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Session MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Session. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Session includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| actor | [Agent](#agent) | The actor, typically a Person or a SoftwareApplication, who initiated the Session.  It is RECOMMENDED that the actor be specified. |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | Represents when this Session commenced.  A start time SHOULD be provided.  If a start time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | Represents when this Session ended or was terminated.  For a [loggedOut](#loggedOut) or [timedOut](#timedOut) action an end time SHOULD be provided.  If an end time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | Represents the total interval of time required to complete this Attempt.  If a duration is specified the value MUST conform to the ISO-8601 duration format. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/sessions/1f6442a482de72ea6ad134943812bff564a76259",
  "@type": "http://purl.imsglobal.org/caliper/v1/Session",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "startedAtTime": "2016-09-15T10:00:00.000Z"
}
```

<a name="sharedAnnotation" />
### SharedAnnotation
A Caliper SharedAnnotation represents the act of sharing a reference to a DigitalResource with other agents.  SharedAnnotation inherits all the properties and requirements defined for [Annotation](#annotation), its superclass.

#### subClassOf
[Annotation](#annotation)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A SharedAnnotation SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a SharedAnnotation MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SharedAnnotation. |
| actor | [Person](#person) | The Person who created the Annotation MUST be specified. |
| annotated | [DigitalResource](#digitalResource) | The DigitalResource that was annotated MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from Annotation](#annotation), SharedAnnotation includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| withAgents | List&lt;[Agent](#agent)&gt; | The ordered set of one or more agents, typically of type Person, with whom the annotated DigitalResource has been shared. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/users/554433/etexts/201/shares/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/SharedAnnotation",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "annotated": {
    "@id": "https://example.edu/etexts/201.epub",
    "@type": "http://purl.imsglobal.org/caliper/v1/Document"
  },
  "withAgents": [
    {
      "@id": "https://example.edu/users/657585",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    {
      "@id": "https://example.edu/users/667788",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    }
  ],
  "dateCreated": "2016-08-01T09:00:00.000Z"
}
```

<a name="softwareapplication" />
#### SoftwareApplication
A Caliper SoftwareApplication represents a computer program, application, module, platform or system.  SoftwareApplication inherits all the properties and requirements defined for [Agent](#agent), its superclass.  It is analogous to a [sdo:SoftwareApplication](http://schema.org/SoftwareApplication) or [dcmitype:Software](http://purl.org/dc/dcmitype/Software).

#### subClassOf
[Agent](#agent)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A SoftwareApplication SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a SoftwareApplication MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SoftwareApplication. |

#### Optional properties
Inherited from [Agent](#agent).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/autograder",
  "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
  "name": "Auto Grader",
  "description": "Automates assignment scoring.",
  "version": "2.5.2"
}
```

<a name="tagAnnotation" />
### TagAnnotation
A Caliper TagAnnotation represents the act of tagging a DigitalResource with tags or labels.  TagAnnotation inherits all the properties and requirements defined for [Annotation](#annotation), its superclass.

#### subClassOf
[Annotation](#annotation)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A TagAnnotation SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a TagAnnotation MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/TagAnnotation. |
| actor | [Person](#person) | The Person who created the Annotation MUST be specified. |
| annotated | [DigitalResource](#digitalResource) | The DigitalResource that was annotated MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from Annotation](#annotation), TagAnnotation includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| tags | List&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt; | The ordered set of one or more tags associated with the annotated DigitalResource. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/users/554433/etexts/201/tags/3",
  "@type": "http://purl.imsglobal.org/caliper/v1/TagAnnotation",
  "actor": {
    "@id": "https://example.edu/users/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person"
  },
  "annotated": {
    "@id": "https://example.edu/etexts/201.epub#epubcfi(/6/4[chap01]!/4[body01]/12[para06]/1:97)",
    "@type": "http://purl.imsglobal.org/caliper/v1/Chapter"
  },
  "tags": [ "profile", "event", "entity" ],
  "dateCreated": "2016-08-01T09:00:00.000Z"
}
```

<a name="thread" />
### Thread
A Caliper Thread represents a series of one or more messages that share a common subject and are connected by a reply or by date relationships.  Thread inherits all the properties and requirements defined for [DigitalResourceCollection](#digitalResourceCollection), its superclass.  It is analogous to a [sioc:Thread](http://rfds.org/sioc/spec/#term_Thread).

#### subClassOf 
[DigitalResourceCollection](#digitalResourceCollection)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A Thread SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a Thread MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Thread. |

#### Optional properties
Inherited from [DigitalResourceCollection](#digitalResourceCollection).

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| items | List&lt;[Message](#message)&gt; | The ordered set of posts that comprise this Thread. |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
  "name": "Caliper Information Model",
  "items": [
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Message"
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/Message",
      "replyTo": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Message"
      }
    },
    {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/Message",
      "replyTo": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1/topics/1/messages/2",
        "@type": "http://purl.imsglobal.org/caliper/v1/Message"
      }
    }
  ],
  "isPartOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/forums/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
    "name": "Caliper Forum",
    "isPartOf": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
      "subOrganizationOf": {
        "@id": "https://example.edu/terms/201601/courses/7",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering"
      }
    }
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="trueFalseResponse" />
### TrueFalseResponse
A Caliper TrueFalseResponse represents a response to a question in which only two possible options are provided (true/false, yes/no).   TrueFalseResponse inherits all the properties and requirements defined for [Response](#response), its superclass.

#### subClassOf 
[Response](#response)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A  TrueFalseResponse SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a  TrueFalseResponse MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/ TrueFalseResponse. |
| attempt | [Attempt](#attempt) | The associated Attempt MUST be specified.  The Attempt MUST reference both the Person who initiated the Response and the DigitalResource that constitutes the object of the assignment.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Response](#response), SelectTextResponse includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| value | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The true/false, yes/no binary selection that constitutes the response MAY be provided.  |

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/5/users/554433/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/TrueFalseResponse",
  "attempt": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/5/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": {
      "@id": "https://example.edu/users/554433",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
      "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1/items/5",
      "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
      "isPartOf": {
        "@id": "https://example.edu/terms/201601/courses/7/sections/1/assess/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
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
### VideoObject
A Caliper VideoObject represents a visual recording stored in digital form. VideoObject inherits all the properties and requirements defined for [MediaObject](#mediaObject), its superclass.  It is analogous to [sdo:VideoObject](http://schema.org/VideoObject).

#### subClassOf 
[MediaObject](#mediaObject)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An VideoObject SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an VideoObject MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/VideoObject. |

#### Optional properties
Inherited from [MediaObject](#mediaObject).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/videos/1225",
  "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
  "mediaType": "video/ogg",
  "name": "Introduction to IMS Caliper",
  "version": "1.1",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z",
  "duration": "PT1H12M27S"
}
```

<a name="webPage" />
### WebPage
A Caliper WebPage represents a document containing markup that is suitable for display in a web browser.  WebPage inherits all the properties and requirements defined for [DigitalResource](#digitalResource), its superclass.  It is analogous to a [sdo:WebPage](http://schema.org/WebPage).

#### subClassOf 
[DigitalResource](#digitalResource)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A WebPage SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a WebPage MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/WebPage. |

#### Optional properties
Inherited from [DigitalResource](#digitalResource).

#### Example
```json
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/201601/courses/7/sections/1/pages/index.html",
  "@type": "http://purl.imsglobal.org/caliper/v1/WebPage",
  "name": "CPS 435-01 Landing Page",
  "mediaType": "text/html",
  "isPartOf": {
    "@id": "https://example.edu/terms/201601/courses/7/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "courseNumber": "CPS 435-01",
    "academicSession": "Fall 2016"
  }
}
```

<a name="appendixZ" />
## Appendix A.  Miscellaneous Classes
TODO Intro

### TextPositionSelector
TODO Intro

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| start | [xsd:nonNegativeInteger]( https://www.w3.org/TR/xmlschema11-2/#nonNegativeInteger) | TODO The start position . . . MUST be specified. |
| end | [xsd:nonNegativeInteger]( https://www.w3.org/TR/xmlschema11-2/#nonNegativeInteger) | ODO The end position . . . MUST be specified. |

```json
{
    "start": "455",
    "end": "489"
}
```

<a name="appendixRoles" />
## Appendix B.  Roles

### Status
The status of a [member](#member) within an organization can be set to one of the following states: active, deleted or inactive.  The value MUST be set to the appropriate IRI:

| Status | IRI |
| ------  | --- | 
| active | http://purl.imsglobal.org/vocab/lis/v2/status#Active |
| deleted | http://purl.imsglobal.org/vocab/lis/v2/status#Deleted |
| inactive | http://purl.imsglobal.org/vocab/lis/v2/status#Inactive |

### Roles
One or more roles assigned to a [member](#member) of an organization can be specified.  Typical roles include learner, instructor, teaching assistant, mentor or administrator.  The value MUST be set to the appropriate IRI:

| Role | IRI |
| ----  | --- | 
| learner | http://purl.imsglobal.org/vocab/lis/v2/membership#Learner |
| external_learner | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#ExternalLearner |
| guest_learner | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#GuestLearner |
| learner_instructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#Instructor |
|  learner_learner | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#Learner |
| noncredit_learner  | http://purl.imsglobal.org/vocab/lis/v2/membership/Learner#NonCreditLearner |

| Role | IRI |
| ----  | --- | 
| instructor | http://purl.imsglobal.org/vocab/lis/v2/membership#Instructor |
| external_instructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#ExternalInstructor |
| guest_instructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#GuestInstructor |
| lecturer | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#Lecturer |
| primary_instructor | http://purl.imsglobal.org/vocab/lis/v2/membership/Instructor#PrimaryInstructor |

| Role | IRI |
| ----  | --- | 
| administrator | http://purl.imsglobal.org/vocab/lis/v2/membership#Administrator |
| administrator_administrator | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#Administrator |
| administrator_developer | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#Developer |
| administrator_support | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#Support |
| administrator_system_administrator | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#SystemAdministrator |
| administrator_external_developer | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#ExternalSupport |
| administrator_external_support | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#ExternalDeveloper |
| administrator_external_system_administrator | http://purl.imsglobal.org/vocab/lis/v2/membership/Administrator#ExternalSystemAdministrator |

| Role | IRI |
| ----  | --- | 
| content_developer | http://purl.imsglobal.org/vocab/lis/v2/membership#ContentDeveloper |
| content_developer_content_developer | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#ContentDeveloper |
| content_developer_ librarian | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#Librarian |
| content_developer_ content_expert | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#ContentExpert |
| content_developer_external_context_expert | http://purl.imsglobal.org/vocab/lis/v2/membership/ContentDeveloper#ExternalContentExpert |

| Role | IRI |
| ----  | --- | 
| manager | http://purl.imsglobal.org/vocab/lis/v2/membership#Manager |
| manager_area_manager | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#AreaManager |
| manager_course_coordinator | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#CourseCoordinator |
| manager_observer | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#Observer",
| manager_external_observer | http://purl.imsglobal.org/vocab/lis/v2/membership/Manager#ExternalObserver |

| Role | IRI |
| ----  | --- | 
| member | http://purl.imsglobal.org/vocab/lis/v2/membership#Member |
| member_member | http://purl.imsglobal.org/vocab/lis/v2/membership/Member#Member |

| Role | IRI |
| ----  | --- | 
| mentor | http://purl.imsglobal.org/vocab/lis/v2/membership#Mentor |
| mentor_mentor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Mentor |
| mentor_external_mentor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalMentor |
| mentor_advisor |  http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Advisor |
| mentor_external_ advisor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalAdvisor |
| mentor_auditor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Auditor |
| mentor_external_auditor | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalAuditor |
| mentor_reviewer |  http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Reviewer |
| mentor_external_reviewer | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalReviewer |
| mentor_tutor |  http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#Tutor |
| mentor_external_tutor | "http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#ExternalTutor |
| mentor_learning_facilitator | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor#LearningFacilitator |
| mentor_external_learning_facilitator | http://purl.imsglobal.org/vocab/lis/v2/membership/Mentor/ExternalLearningFacilitator |

| Role | IRI |
| ----  | --- | 
| teaching_assistant | http://purl.imsglobal.org/vocab/lis/v2/membership#TeachingAssistant |
| teaching_assistant_teaching_assistant | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistant |
| teaching_assistant_grader | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#Grader |
| teaching_assistant_teaching_assistant_section | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantSection |
| teaching_assistant_teaching_assistant_section_association | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantSectionAssociation |
| teaching_assistant_teaching_assistant_offering | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantOffering |
| teaching_assistant_teaching_assistant_template | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantTemplate |
| teaching_assistant_teaching_assistant_group | http://purl.imsglobal.org/vocab/lis/v2/membership/TeachingAssistant#TeachingAssistantGroup |

<a name="revisionHistory" />
## Revision History

### Deprecations and Removals

#### Profiles
| Profile | Deprecated | Removed | Notes |
| -------  | --------------- | ------------- | -------- |
| [AssessmentItem Profile](#assessmentItemProfile)  | 1.1 | 1.1 | [AssessmentItemEvent] moved to [AssessmentProfile](#assessmentProfile) rendering the AssessmentItem Profile redundant. |

#### Events
| Event | Deprecated | Removed | Notes |
| -------  | --------------- | ------------- | -------- |
| [ReadingEvent](#readingEvent)  | 1.1 | &nbsp; | &nbsp; |

#### Entities
| Event | Deprecated | Removed | Notes |
| -------  | --------------- | ------------- | -------- |
| [EpubChapter](#epubChapter) | 1.1 | &nbsp; | Deprecated in favor of [Chapter](#chapter) |
| [EpubPart](#epubPart) | 1.1 | &nbsp; | &nbsp; |
| [EpubSubchapter](#epubSubchapter) | 1.1 | &nbsp; | &nbsp; |
| [EpubVolume](#epubVolume) | 1.1 | &nbsp; | &nbsp; |
| [Reading](#reading) | 1.1 | &nbsp; | Deprecated in favor of [Document](#document) |

#### Actions
| Event | actions | Deprecated | Removed | Notes |
| -----  | ------- | ------------ | --------- | ------ |
| [AssignableEvent](#assignableEvent) | [abandoned](#abandoned), [reviewed](#reviewed), [hid](#hid),  [showed](#showed] | 1.1 | &nbsp; | &nbsp; |

#### Data Properties
| Event | Deprecated | Removed | Notes |
| -------  | --------------- | ------------- | -------- |
| [objectType](#objectType)  | 1.1 | &nbsp; | &nbsp; |

<a name="reference" />
### References
<a name="json-ld">
__JSON-LD__  W3C.  M. Sporny, D. Longley, G. Kellog, M. Lanthaler, N. Lindström. JSON-LD 1.0. A JSON-based Serialization for Linked Data. 16 January 2014.  URL. https://www.w3.org/TR/json-ld/.

<a name="lti">
__LTI__  TODO

<a name="rfc2119">
__RFC 2119__ IETF.  S. Bradner. "Key words for use in RFCs to Indicate Requirement Levels". March 1997. URL: https://tools.ietf.org/html/rfc2119.