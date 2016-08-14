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
* 4.0 [Profiles](#profiles)
	* 4.1 [Basic Profile](#basicProfile)
	* 4.2 [Annotation Profile](#annotationProfile)
	* 4.3 [Assignable Profile](#assignableProfile)
	* 4.4 [Assessment Profile](#assessmentProfile)
	* 4.5 [Content Management Profile](#contentMgmtProfile)
	* 4.6 [Discussion Forum Profile](#discussionForumProfile)
	* 4.7 [Media Profile](#mediaProfile)
	* 4.8 [Outcome Profile](#outcomeProfile)
	* 4.9 [Reading Profile](#readingProfile)
	* 4.10 [Session Profile](#sessionProfile)
* 5.0 [Events](#events)
	* 5.1 [Event](#event)
	* 5.2 [AnnotationEvent](#annotationEvent)
	* 5.3 [AssessmentEvent](#assessmentEvent)
	* 5.4 [AssessmentItemEvent](#assessmentItemEvent)
    * 5.5 [AssignableEvent](#assignableEvent)
	* 5.6 [DigitalResourceMgmtEvent](#digitalResourceMgmtEvent)
	* 5.7 [ForumEvent](#ForumEvent)
	* 5.8 [MediaEvent](#mediaEvent)
	* 5.9 [MessageEvent](#messageEvent)
	* 5.10 [NavigationEvent](#navigationEvent)
	* 5.11 [OutcomeEvent](#outcomeEvent)
	* 5.12 [SessionEvent](#sessionEvent)
	* 5.13 [ThreadEvent](#ThreadEvent)
	* 5.14 [ViewEvent](#viewEvent)
* 6.0 [Actions](#actions)
* 7.0 [Entities](#entities)    
* 8.0 [Sensor API](#api)
* 9.0 [Transport](#transport)
    * 9.1 [Envelope](#envelope)
	* 9.2 [Endpoints](#endpoints)
* 10.0 [Contributors](#contributors)
* [Appendix A: Caliper Entities](#appendixA)
* [Appendix B: Miscellaneous Classes](#appendixB)
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
| clpr | http://purl.imsglobal.org/caliper/v1/ | Caliper |
| clpract | http://purl.imsglobal.org/vocab/caliper/v1/action# | Caliper actions |
| clprlis | http://purl.imsglobal.org/caliper/v1/ | Caliper LIS |
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

### 1.2 Terminology
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](#rfc2119).  A Sensor implementation that fails to implement a MUST/REQUIRED/SHALL requirement or fails to abide by a MUST NOT/SHALL NOT prohibition is considered non-conformant.  SHOULD/SHOULD NOT/RECOMMENDED statements constitute a best practice.  Ignoring a best practice does not violate conformance but a decision to disregard such guidance should be carefully considered.  MAY/OPTIONAL statements indicate that implementors are entirely free to choose whether or not to implement the option.

<a name="definitions"/>  
### 1.3 Definitions
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
## 2.0 Data and Semantic Interoperability

TODO

structure, flow, pointers

<a name="infoModel">
## 3.0 Information Model

TODO: OVERVIEW 

<a name="profiles" />
## 4.0 Profiles
The Caliper Information Model is comprised of a number of activity profiles, each of which models a particular learning or supporting activity.  Each profile provides a common/structured vocabularly / concepts and terms for describing events such as annotating a document, starting an assessment or grading an outcome.  Extending the model involves adding a new profile or enhancing an existing one.

TODO: ADDITIONAL INTRO TEXT

[Basic](#basicProfile), [Annotation](#annotationProfile), [Assessment](#annotationProfile), [Assignable](#assignableProfile), [Content Management](#contentMgmtProfile), [Discussion Forum](#discussionForumProfile), [Media](#mediaProfile), [Outcome](#outcomeProfile), [Reading](#readingProfile), [Session](#sessionProfile)

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

### OR  

#### Supported object, generated, target and referrer entities
| Event | action | object | generated | target | referrer |
| ----- | -------| ------ | ----------- | ------ | ------- |
|  [AssessmentEvent](#assessmentEvent) | [started](#started), [paused](#paused), [restarted](#restarted), [submitted](#submitted) | [Attempt](#attempt) | &nbsp; | &nbsp; | &nbsp; |
|  [AssessmentItemEvent](#assessmentItemEvent) | [started](#started), [skipped](#skipped),  [completed](#completed) | [Attempt](#attempt) | &nbsp;  | &nbsp; | &nbsp; |
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

#### TODO
* Decide if [Attempt](#attempt) should always be the object.

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

#### OR

#### Supported object, generated, target and referrer entities
| Event | action | object | generated | target | referrer |
| ----- | -------| ------ | ----------- | ------ | ------- |
|  [AssignableEvent](#assignableEvent)  | [started](#started), [completed](#completed) | [Attempt](#attempt) | &nbsp; | &nbsp; | &nbsp; |
|  [AssignableEvent](#assignableEvent)  | [activated](#activated), [deactivated](#deactivated) | [DigitalResource](#digitalResource) | &nbsp;  | &nbsp; | &nbsp; |
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
* Decide whether Attempt should be the object of the interaction
* Do we need to add a submitted action?

<a name="contentManagementProfile" />
### 4.5 Content Management Profile / Content Authoring Profile
The Content Management Profile models activities associated with the creation and management of digital content.

#### Supported Events
[ContentMgmtEvent](#contentMgmtEvent), [NavigationEvent](#navigationEvent), [ViewEvent](#ViewEvent)

#### Supported Actions
| Event | action(s) |
| -----  | --------- |
| [ContentMgmtEvent](#contentMgmtEvent) | [created](#created), [modified], (#modified), [published](#published), [retrieved](#retrieved), [removed](#removed), [deleted](#deleted) |
| [NavigationEvent](#navigationEvent) | [navigatedTo](#navigatedTo) |
| [ViewEvent](#ViewEvent) | [viewed](#viewed) |

#### Supported object, generated, target and referrer entities
| Event | object | generated | target | referrer |
| ----- | ------ | ----------- | ------ | ------- |
| [ContentMgmtEvent](#contentMgmtEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | &nbsp; |
| [NavigationEvent](#navigationEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | [DigitalResource](#digitalResource) |
| [ViewEvent](#ViewEvent) | [DigitalResource](#digitalResource) | &nbsp; | &nbsp; | &nbsp; 

#### Example Sequence
 Note: *setting optional [Event](#event) properties that provide additional contextual information is assumed in example sequence*.
 
| Event | actor | action | object | eventTime |
| -----  | ----- | ------ | ------ | ----------- |
| [ContentMgmtEvent](#digitalResourceMgmtEvent)  | [Person](#person) P1 | [created](#created) | [Document](#document) D1 | [dateTime](#dateTime) T1 |
| [ContentMgmtEvent](#digitalResourceMgmtEvent) | [Person](#person) P2 | [retrieved](#retrieved) | [Document](#document) D1 | [dateTime](#dateTime) T2 |
| [ContentMgmtEvent](#digitalResourceMgmtEvent)  | [Person](#person) P2 | [modified](#modified)| [Document](#document) D1 | [dateTime](#dateTime) T3 |
| [ContentMgmtEvent](#digitalResourceMgmtEvent)  | [Person](#person) P1 | [published](#published) | [Document](#document) D1 | [dateTime](#dateTime) T4 |
| [NavigationEvent](#navigationEvent) | [Person](#person) P3 | [navigatedTo](#navigatedTo) | [Document](#document) D1 | [dateTime](#dateTime) T5 |
| [ViewEvent](#viewEvent)| [Person](#person) P3 | [viewed](#viewed) | [Document](#document) D1 | [dateTime](#dateTime) T6 |

#### TODO
* consider renaming to "Entity Management Profile" and widening object scope from [DigitalResource](#digitalResource) to [Entity](#entity).
* consider renaming to "Content Authoring Profile" . . . .

<a name="discussionForumProfile" />
### 4.6 Discussion Forum Profile
The online discussion forum is a core capability of many learning management systems.  Forums typically encompass one or more topics to which actors can subscribe, post messages and reply to other messages if a threaded discussion is permitted.  The profile leverages a number of Caliper [Event](#event) types to describe users participating in online forum communities.

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
TODO: OVERVIEW

<a name="event"/>
### 5.1 Event
A Caliper Event is a generic class that represents the interaction between an [actor](#actor) and an [object](#object) at a specific moment in time and within the bounds of a specified context. For enhanced specificity implementors SHOULD utilize the several subclasses of Event rather than instantiating instances of the Event class itself.

For an Event to be minimally compliant it MUST specify an [actor](#actor), [action](#action), [object](#object) and an [eventTime](#eventTime).

### Supported actions
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

##### Subclasses
[AnnotationEvent](#annotationEvent), [AssignableEvent](#assignableEvent), [AssignmentEvent](#assignmentEvent), [AssignmentItemEvent](#assignmentItemEvent), [ContentMgmtEvent](#contentMgmtEvent), [ForumEvent](#forumEvent), [MediaEvent](#mediaEvent), [MessageEvent](#messageEvent), [NavigationEvent](#navigationEvent), [OutcomeEvent](#outcomeEvent), [ReadingEvent](#readingEvent), [SessionEvent](#sessionEvent), [ThreadEvent](#threadEvent), [ViewEvent](#viewEvent)

##### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/ViewEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed",
    "object": {
        "@id": "http://do1.dr-chuck.com/pythonlearn/EN_us/pythonlearn.pdf",
        "@type": "http://purl.imsglobal.org/caliper/v1/Document",
        "name": "Python for Everybody.  Exploring Data using Python 3",
        "version": "2016-Jul-05 First Complete Python 3.0 version"
    },
    "eventTime": "2016-09-15T10:15:00.000Z"
}
```

<a name="annotationEvent" />
### 5.2 AnnotationEvent
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/AnnotationEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1/resources/1/book011.html",
        "@type": "http://purl.imsglobal.org/caliper/v1/Chapter",
        "name": "Chapter 10. Tuples"
    },
    "generated": {
        "@id": "https://example.edu/tags/7654",
        "@type": "http://purl.imsglobal.org/caliper/v1/TagAnnotation",
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "annotated": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1/resources/1/book011.html",
            "@type": "http://purl.imsglobal.org/caliper/v1/Chapter"
        },
        "tags": [ "csev", "python" "tuple", "dictionaries" ],
        "dateCreated": "2016-09-17T10:15:12.000Z"
    },
    "eventTime": "2016-09-17T10:15:12.000Z",
    "edApp": {
        "@id": "https://example.edu/",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/973465e7f388940324465caf55b4f761b0f4f093",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-17T10:00:00.000Z"
    }
}
```
	
<a name="assessmentEvent" />
### 5.3 AssessmentEvent
The AssessmentEvent models learner interactions with assessments instruments such as online tests or quizzes.  AssessmentEvent inherits all the properties and requirements defined for Event, its superclass.  

#### TODO
* Add additional intro text
* Confirm: Attempt as the object.

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
| object | [Assessment](#assessment) | &nbsp; | 
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

#### OR

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssessmentEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this AssessmentEvent. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Started |
| object | [Attempt](#attempt) | The learner's Attempt MUST reference both the actor and the assigned Assessment.  A [count](#count) of the number of times the actor has interacted with the Assessment MUST also be specified. | 
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
| federatedSession | [LtiSession](#ltiSession) |If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Started",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/assessments/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
        "name": "Quiz One",
        "dateToStartOn": "2016-09-16T05:00:00.000Z",
        "dateToSubmit": "2016-09-18T11:59:59.000Z",
        "maxAttempts": 2,
        "maxSubmits": 2,
        "maxScore": 25,
        "version": "1.0"
    },
    "generated": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1/users/554433/attempts/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
        "assignable": {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
        },
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "count": 1,
        "dateCreated": "2016-09-17T10:15:00.000Z",
        "startedAtTime": "2016-09-17T10:15:00.000Z"
    },
    "eventTime": "2016-09-17T10:15:00.000Z",
    "edApp": {
        "@id": "https://example.edu/",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/973465e7f388940324465caf55b4f761b0f4f093",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-17T10:00:00.000Z"
    }
}
```
#### OR
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Started",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1/users/554433/attempts/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
        "assignable": {
            "@id": "https://example.edu/semesters/201601/courses/301/assessments/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
            "name": "Quiz One",
            "dateToStartOn": "2016-09-16T05:00:00.000Z",
            "dateToSubmit": "2016-09-18T11:59:59.000Z",
            "maxAttempts": 2,
            "maxSubmits": 2,
            "maxScore": 25,
            "version": "1.0"
        },
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "count": 1,
        "dateCreated": "2016-09-17T10:15:00.000Z",
        "startedAtTime": "2016-09-17T10:15:00.000Z"
    },
    "eventTime": "2016-09-17T10:15:00.000Z",
    "edApp": {
        "@id": "https://example.edu/",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/973465e7f388940324465caf55b4f761b0f4f093",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-17T10:00:00.000Z"
    }
}
```

<a name="assessmentItemEvent" />
### 5.4 AssessmentItemEvent
The AssessmentItemEvent models a learner's interaction with an individual assessment item.  AssessmentItemEvent inherits all the properties and requirements defined for Event, its superclass.  

#### TODO
* Confirm: Attempt as the object.
* Confirm: "The Attempt MAY also reference a parent Attempt via the [isPartOf](#isPartOf) property."
* Confirm: ". . . for a [completed](#completed) action it is RECOMMENDED that the [Attempt](#attempt) comprise the object."  (rationale: if generated is optional how can we require an Attempt).

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
| object | [AssessmentItem](#assessmentItem), [Attempt](#attempt) | For [started](#started) and [skipped] actions the AssessmentItem is the REQUIRED object of the interaction; for a [completed](#completed) action it is RECOMMENDED that the learner's [Attempt](#attempt) comprise the object.  
If the Attempt is provided it MUST reference both the actor and the assigned AssessmentItem.  A [count](#count) of the number of times the actor has interacted with the AssessmentItem MUST also be specified.  The Attempt MAY also reference a parent Attempt via the [isPartOf](#isPartOf) property. | 
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

### OR

| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/AssessmentItemEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this AssessmentItemEvent. |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Completed |
| object | [Attempt](#attempt) | The learner's Attempt MUST be specified in order to record a [count](#count) of the number of times the actor has interacted with the AssessmentItem.  The Attempt MUST reference both the actor and the AssessmentItem to which the Attempt refers. The Attempt MAY also reference a parent Attempt via the [isPartOf](#isPartOf) property. | 
| eventTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision.  |

#### Optional properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| target | &nbsp; | &nbsp;  |
| generated | [Response](#response) | For a [completed](#completed) action a generated Response MAY be referenced.  Note that Response is a generic type that is subclassed for greater type specificity.  Utilize Response only if no suitable subclass exists to represent the learner's response to the item. |
| referrer | [Entity](#entity) | A SoftwareApplication or a subclass of DigitalResource will typically constitute the referring context.  Note that both Entity and DigitalResource are generic types that are subclassed for greater type specificity.  Utilize Entity or DigitalResource only if no suitable subclass exists to represent the referrer. |
| edApp | [SoftwareApplication](#softwareApplication) | &nbsp; |
| group | [Organization](#organization) | Organization is a generic type that is subclassed for greater type specificity.  Utilize Organization only if no suitable subclass exists to represent the group context.  |
| membership | [Membership](#membership) | &nbsp; |
| session | [Session](#session)| &nbsp; | 
| federatedSession | [LtiSession](#ltiSession) | If the Event occurs within the context of an LTI(#lti) tool launch, the tool consumer Session SHOULD be referenced. | 
| extensions | object | Additional properties not defined by the model MAY be specified for a more concise representation of the Event. | 

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItemEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Completed",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/3/users/554433/attempts/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
        "assignable": {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/3",
            "@type": "http: //purl.imsglobal.org/caliper/v1/AssessmentItem",
            "name": "Assessment Item 3",
            "isPartOf": {
                "@id": "https://example.edu/semesters/201601/courses/301/assess/1",
                "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
            },
            "maxAttempts": 2,
            "maxSubmits": 2,
            "maxScore": 1,
            "isTimeDependent": false
        },
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "count": 1,
        "dateCreated": "2016-09-17T10:15:00.000Z",
        "startedAtTime": "2016-09-17T10:15:00.000Z",
        "endedAtTime": "2016-09-17T10:15:12.000Z"
    },
    "generated": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/3/users/554433/responses/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
        "assignable": {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
        },
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "attempt": {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/3/users/554433/attempts/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Attempt"
        }
    },
    "eventTime": "2016-09-17T10:15:12.000Z",
    "edApp": {
        "@id": "https: //example.edu/",
        "@type": "http: //purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https: //example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http: //purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https: //example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http: //purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https: //example.edu/people/554433",
            "@type": "http: //purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https: //example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http: //purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http: //purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http: //purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https: //example.com/lms/sessions/973465e7f388940324465caf55b4f761b0f4f093",
        "@type": "http: //purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-17T10:00:00.000Z"
    }
}
```

<a name="assignableEvent" />
### 5.5 AssignableEvent
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/AssignableEvent",
    "actor": {
        "@id": "https://example.edu/user/112233",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Activated",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/assessments/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
        "name": "Quiz One",
        "dateCreated": "2016-08-01T06:00:00.000Z",
        "dateModified": "2016-09-02T11:30:00.000Z",
        "datePublished": "2015-09-15T10:10:00.000Z",
        "dateToActivate": "2015-09-15T10:15:00.000Z",
        "dateToStartOn": "2016-09-16T05:00:00.000Z",
        "dateToSubmit": "2016-09-18T11:59:59.000Z",
        "maxAttempts": 2,
        "maxSubmits": 2,
        "maxScore": 25,
        "version": "1.0"
    },
    "eventTime": "2016-09-15T10:15:00.000Z",
    "edApp": {
        "@id": "https://example.edu/",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/112233",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Instructor"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    }
}
```

<a name="contentMgmtEvent" />
### 5.6 ContentMgmtEvent / EntityMgmtEvent

The ContentMgmtEvent models activities associated with the creation and management of digital content.  ContentMgmtEvent inherits all the properties and requirements defined for Event, its superclass.  

TODO add additional intro text

#### Supported actions
[created](#created), [modified](#modified), [published](#published), [retrieved](#retrieved), [removed](#removed), [deleted](#deleted) 

#### Required properties
| Property  | Type | Requirements |
| -------- |  -----  | ----------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context. |
| id | UUID | An id MUST be generated by the endpoint if an Event is received without an id.  The id must be in the form of a UUID in standard string form (see RFC 4122 for requirements). |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/ContentMgmtEvent |
| actor  | [Person](#person) | The Person who initiated or is the subject of this ContentMgmtEvent.  |
| action | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value range is limited to the supported actions listed above.  The value assigned MUST be the appropriate IRI, e.g., http://purl.imsglobal.org/vocab/caliper/v1/action#Created |
| object | [DigitalResource](#digitalResource) | DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. | 
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/ContentMgmtEvent",
    "actor": {
        "@id": "https://example.edu/user/112233",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Published",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/resources/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResourceCollection",
        "name": "Course resources",
        "creators": [
            {
                "@id": "https://example.edu/user/112233",
                "@type": "http://purl.imsglobal.org/caliper/v1/Person"
            },
            {
                "@id": "https://example.edu/user/223344",
                "@type": "http://purl.imsglobal.org/caliper/v1/Person"
            }
        ],
        "keywords": [ "collections", "documents", "images", "videos"],
        "items": [
            {
                "@id": "https://example.edu/semesters/201601/courses/301/resources/1/collections/1",
                "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResourceCollection",
                "name": "Document Collection",
                "dateCreated": "2016-08-01T06:01:00.000Z",
                "datePublished": "2016-08-15T09:30:00.000Z"
            },
            {
                "@id": "https://example.edu/semesters/201601/courses/301/resources/1/collections/2",
                "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResourceCollection",
                "name": "Image Collection",
                "dateCreated": "2016-08-01T06:02:00.000Z",
                "datePublished": "2016-08-15T09:30:00.000Z"
            },
            {
                "@id": "https://example.edu/semesters/201601/courses/301/resources/1/collections/3",
                "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResourceCollection",
                "name": "Video Collection",
                "dateCreated": "2016-08-01T06:03:00.000Z",
                "datePublished": "2016-08-15T09:30:00.000Z"
            }
        ],
        "isPartOf": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "dateCreated": "2016-09-01T08:00:00.000Z",
        "dateModified": "2016-09-01T08:55:00.000Z",
        "datePublished": "2016-09-15T09:00:00.000Z"
    },
    "eventTime": "2016-09-15T09:00:00.000Z",
    "edApp": {
        "@id": "https://example.edu/",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/112233",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Instructor"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/f489527a078617eb8a3c71f1a9aba8e6f166ece2",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-15T07:55:12.000Z"
    }
}
```

<a name="forumEvent" />
### 5.7 ForumEvent

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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/ForumEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/forums/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
        "name": "Caliper Forum",
        "isPartOf": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "dateCreated": "2016-09-14T11:00:00.000Z"
    },
    "eventTime": "2016-09-15T10:16:00.000Z",
    "edApp": {
        "@id": "https://example.com/lms/forums",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/41102ee0870b0be0bb3259166a9947952a3c5425",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-15T10:12:00.000Z"
    }
}
```

<a name="mediaEvent" />
### 5.8 MediaEvent
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

#### Example
```
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/MediaEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Paused",
    "object": {
        "@id": "https://youtu.be/UQVK-dsU7-Y",
        "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
        "name": "Python for Informatics: Information and Welcome",
        "mediaType": "video/ogg",
        "duration": "PT20M20S"
    },
    "target": {
        "@id": "https://youtu.be/UQVK-dsU7-Y?t=321",
        "@type": "http://purl.imsglobal.org/caliper/v1/MediaLocation"
        "currentTime": "PT05M21S"
    },
    "eventTime": "2016-09-15T10:15:00.000Z",
    "edApp": {
        "@id": "http://www.pythonlearn.com/",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/41102ee0870b0be0bb3259166a9947952a3c5425",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-15T10:12:00.000Z"
    }
}
```

<a name="messageEvent" />
### 5.9 MessageEvent
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

#### Example: MessageEvent posted (reply)
```
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/MessageEvent",
    "actor": {
        "@id": "https://example.edu/users/778899",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Posted",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/3",
        "@type": "http://purl.imsglobal.org/caliper/v1/Message",
        "creators": [
            {
                "@id": "https://example.edu/users/778899",
                "@type": "http://purl.imsglobal.org/caliper/v1/Person"
            }
        ],
        "replyTo": {
            "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/2",
            "@type": "http://purl.imsglobal.org/caliper/v1/Message"
        },
        "isPartOf": {
            "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
            "isPartOf": {
                "@id": "https://example.edu/semesters/201601/courses/301/forums/2",
                "@type": "http://purl.imsglobal.org/caliper/v1/Forum"
            }
        },
        "dateCreated": "2016-09-15T10:15:30.000Z"
    },
    "eventTime": "2016-09-15T10:15:30.000Z",
    "edApp": {
        "@id": "https://example.com/lms/forums",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": "https://example.edu/users/778899",
        "organization": "https://example.edu/semesters/201601/courses/301/sections/1",
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/41102ee0870b0be0bb3259166a9947952a3c5425",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-15T10:12:00.000Z"
    }
}
```
<a name="navigationEvent" />
### 5.10 NavigationEvent
The NavigationEvent models an actor traversing a network of digital resources.  NavigationEvent inherits all the properties and requirements defined for Event, its superclass. 

TODO note referrer property

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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/NavigationEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo",
    "object": {
        "@id": "http://do1.dr-chuck.com/pythonlearn/EN_us/pythonlearn.pdf",
        "@type": "http://purl.imsglobal.org/caliper/v1/Document",
        "name": "Python for Everybody.  Exploring Data using Python 3",
        "version": "2016-Jul-05 First Complete Python 3.0 version"
    },
    "eventTime": "2015-09-15T10:15:00.000Z",
    "referrer": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1/pages/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/WebPage",
        "name": "Learn Python Landing Page"
    },
    "edApp": {
        "@id": "https://example.edu/lms",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/41102ee0870b0be0bb3259166a9947952a3c5425",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-15T10:12:00.000Z"
    }
}
```

<a name="outcomeEvent" />
### 5.11 OutcomeEvent
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/OutcomeEvent",
    "actor": {
        "@id": "https://example.com/autograder",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Graded",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1/users/554433/attempts/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
        "assignable": {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
        },
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "count": 1,
        "dateCreated": "2016-09-15T10:05:00.000Z",
        "startedAtTime": "2016-09-15T10:05:00.000Z",
        "endedAtTime": "2016-09-15T10:55:12.000Z",
        "duration": "PT50M12S"
    },
    "eventTime": "2016-09-15T10:57:06.000Z",
    "generated": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1/users/554433/results/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Result",
        "assignable": {
            "@id": "https://example.edu/semesters/201601/courses/301/assessments/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
        },
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "normalScore": 3,
        "totalScore": 3,
        "scoredBy": {
            "@id": "https://example.com/autograder",
            "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
        },
        "dateCreated": "2016-09-15T10:55:05.000Z"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    }
}
```

<a name="sessionEvent" />
### 5.12 SessionEvent
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "id": "15128c13-ca75-4952-8cce-72a513ec337d",
    "@type": "http://purl.imsglobal.org/caliper/v1/SessionEvent",
    "actor": {
        "@id": "https://example.com/viewer",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut",
    "object": {
        "@id": "https://example.com/viewer/sessions/7d6b88adf746f0692e2e873308b78c60fb13a864",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "startedAtTime": "2016-09-15T10:15:00.000Z",
        "endedAtTime": "2016-09-15T11:15:00.000Z",
        "duration": "PT3600S"
    },
    "eventTime": "2016-09-15T11:15:00.000Z",
    "edApp": {
        "@id": "https://example.com/viewer",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
    }
}
```

<a name="threadEvent" />
### 5.13 ThreadEvent
A Caliper ThreadEvent models an actor marking a discussion forum thread as either read or unread.  ThreadEvent inherits all the properties and requirements defined for Event, its superclass.

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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/ThreadEvent",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead",
    "object": {
        "@id": "https://example.edu/semesters/201601/courses/301/forums/1/topics/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
        "name": "Caliper Information Model",
        "isPartOf": {
            "@id": "https://example.edu/semesters/201601/courses/301/forums/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
            "name": "Caliper Forum",
            "dateCreated": "2016-09-15T10:15:00.000Z"
        },
        "dateCreated": "2016-09-15T10:16:00.000Z"
    },
    "eventTime": "2016-09-15T10:16:00.000Z",
    "edApp": {
        "@id": "https://example.com/lms/forums",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication",
        "version": "v2"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/41102ee0870b0be0bb3259166a9947952a3c5425",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-15T10:12:00.000Z"
    }
}
```

<a name="ViewEvent" />
### 5.14 ViewEvent
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@type": "http://purl.imsglobal.org/caliper/v1/ViewEvent",
    "actor": {
        "@id": "https://example.edu/people/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "action": "http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed",
    "object": {
        "@id": "http://do1.dr-chuck.com/pythonlearn/EN_us/pythonlearn.pdf",
        "@type": "http://purl.imsglobal.org/caliper/v1/Document",
        "name": "Python for Everybody.  Exploring Data using Python 3",
        "version": "2016-Jul-05 First Complete Python 3.0 version"
    },
    "eventTime": "2015-09-15T10:15:00.000Z",
    "edApp": {
        "@id": "https://example.com/viewer",
        "@type": "http://purl.imsglobal.org/caliper/v1/SoftwareApplication"
    },
    "group": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "courseNumber": "CPS101-01",
        "academicSession": "Fall-2016"
    },
    "membership": {
        "@id": "https://example.edu/semesters/201601/courses/301/rosters/20",
        "@type": "http://purl.imsglobal.org/caliper/v1/Membership",
        "member": {
            "@id": "https://example.edu/people/554433",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        },
        "organization": {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
        },
        "roles": [
            "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
        ],
        "status": "http://purl.imsglobal.org/vocab/lis/v2/status#Active",
        "dateCreated": "2016-08-01T06:00:00.000Z"
    },
    "session": {
        "@id": "https://example.com/lms/sessions/41102ee0870b0be0bb3259166a9947952a3c5425",
        "@type": "http://purl.imsglobal.org/caliper/v1/Session",
        "startedAtTime": "2016-09-15T10:12:00.000Z"
    }
}
```
<a name="actions"/>   
## 6.0 Actions
TODO DESCRIPTION

| Label | IRI | WordNet Gloss |
| ------ | --- | ------------- |
| <a name="abandoned" />abandoned | [http://purl.imsglobal.org/vocab/caliper/v1/action#Abandoned](http://purl.imsglobal.org/vocab/caliper/v1/action#Abandoned) |  |
| <a name="activated" />activated | [http://purl.imsglobal.org/vocab/caliper/v1/action#Activated](http://purl.imsglobal.org/vocab/caliper/v1/action#Activated) |  |
| <a name="attached" />attached | [http://purl.imsglobal.org/vocab/caliper/v1/action#Attached](http://purl.imsglobal.org/vocab/caliper/v1/action#Attached) |  |
| <a name="bookmarked" />bookmarked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Bookmarked](http://purl.imsglobal.org/vocab/caliper/v1/action#Bookmarked) |  |
| <a name="changedResolution" />changed resolution | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedResolution](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedResolution) | |
| <a name="changedSize" />changed size | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSize](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSize) | |
| <a name="changedSpeed" />changed speed | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSpeed](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedSpeed) | |
| <a name="changedVolume" />changed volume | [http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedVolume](http://purl.imsglobal.org/vocab/caliper/v1/action#ChangedVolume) | |
| <a name="classified" />classified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Classified](http://purl.imsglobal.org/vocab/caliper/v1/action#Classified) | |
| <a name="closedPopout" />closed popout | [http://purl.imsglobal.org/vocab/caliper/v1/action#ClosedPopout](http://purl.imsglobal.org/vocab/caliper/v1/action#ClosedPopout) | |
| <a name="commented" />commented | [http://purl.imsglobal.org/vocab/caliper/v1/action#Commented](http://purl.imsglobal.org/vocab/caliper/v1/action#Commented) | |
| <a name="completed" />completed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Completed](http://purl.imsglobal.org/vocab/caliper/v1/action#Completed) | |
| <a name="created" />created | [http://purl.imsglobal.org/vocab/caliper/v1/action#Created](http://purl.imsglobal.org/vocab/caliper/v1/action#Created) | [make or cause to be or to become](http://wordnet-rdf.princeton.edu/wn31/201620211-v) |
| <a name="deactivated" />deactivated | [http://purl.imsglobal.org/vocab/caliper/v1/action#Deactivated](http://purl.imsglobal.org/vocab/caliper/v1/action#Deactivated) | |
| deleted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted](http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted) | [wipe out digitally](http://wordnet-rdf.princeton.edu/wn31/201001860-v) |
| <a name="described" />described | [http://purl.imsglobal.org/vocab/caliper/v1/action#Described](http://purl.imsglobal.org/vocab/caliper/v1/action#Described) | |
| <a name="disabledClosedCaptioning" />disabled closed captioning | [http://purl.imsglobal.org/vocab/caliper/v1/action#DisabledClosedCaptioning](http://purl.imsglobal.org/vocab/caliper/v1/action#DisabledClosedCaptioning) | |
| <a name="disliked" />disliked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Disliked](http://purl.imsglobal.org/vocab/caliper/v1/action#Disliked) | |
| <a name="enabledClosedCaptioning" />enabled closed captioning | [http://purl.imsglobal.org/vocab/caliper/v1/action#EnabledClosedCaptioning](http://purl.imsglobal.org/vocab/caliper/v1/action#EnabledClosedCaptioning) | |
| <a name="ended" />ended | [http://purl.imsglobal.org/vocab/caliper/v1/action#Ended](http://purl.imsglobal.org/vocab/caliper/v1/action#Ended) | |
| <a name="enteredFullscreen" />entered full screen | [http://purl.imsglobal.org/vocab/caliper/v1/action#EnteredFullscreen](http://purl.imsglobal.org/vocab/caliper/v1/action#EnteredFullscreen) | |
| <a name="exitedFullscreen" />exited full screen | [http://purl.imsglobal.org/vocab/caliper/v1/action#ExitedFullscreen](http://purl.imsglobal.org/vocab/caliper/v1/action#ExitedFullscreen) | |
| <a name="forwardedTo" />forwarded to | [http://purl.imsglobal.org/vocab/caliper/v1/action#ForwardedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#ForwardedTo) | |
| <a name="graded" />graded | [http://purl.imsglobal.org/vocab/caliper/v1/action#Graded](http://purl.imsglobal.org/vocab/caliper/v1/action#Graded) | |
| <a name="hid" />hid | [http://purl.imsglobal.org/vocab/caliper/v1/action#Hid](http://purl.imsglobal.org/vocab/caliper/v1/action#Hid) | |
| <a name="highlighted" />highlighted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Highlighted](http://purl.imsglobal.org/vocab/caliper/v1/action#Highlighted) | |
| <a name="jumpedTo" />jumped to | [http://purl.imsglobal.org/vocab/caliper/v1/action#JumpedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#JumpedTo) | |
| <a name="identified" />identified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Identified](http://purl.imsglobal.org/vocab/caliper/v1/action#Identified) | |
| <a name="liked" />liked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Liked](http://purl.imsglobal.org/vocab/caliper/v1/action#Liked) | |
| <a name="linked" />linked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Linked](http://purl.imsglobal.org/vocab/caliper/v1/action#Linked) | |
| <a name="loggedIn" />logged in | [http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedIn) | [enter a computer or software application](http://wordnet-rdf.princeton.edu/wn31/202253955-v) |
| <a name="loggedIn" />logged out | [http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut](http://purl.imsglobal.org/vocab/caliper/v1/action#LoggedOut) | [exit a computer or software application](http://wordnet-rdf.princeton.edu/wn31/202254101-v) |
| <a name="markedAsRead" />marked as read | [http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead) | [mark: designate as if by a mark](http://wordnet-rdf.princeton.edu/wn31/200923709-v), [read: interpret something that is written or printed](http://wordnet-rdf.princeton.edu/wn31/200626756-v) |
| <a name="markedAsUnread" />marked as unread | [http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread](http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread) | inverse of markedAsRead |
| <a name="modified" />modified | [http://purl.imsglobal.org/vocab/caliper/v1/action#Modified](http://purl.imsglobal.org/vocab/caliper/v1/action#Modified) | [cause to change; make different; cause a transformation](http://wordnet-rdf.princeton.edu/wn31/200126072-v) |
| <a name="muted" />muted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Muted](http://purl.imsglobal.org/vocab/caliper/v1/action#Muted) | |
| <a name="navigated to" />navigated to | [http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo](http://purl.imsglobal.org/vocab/caliper/v1/action#NavigatedTo) | |
| <a name="openedPopout" />opened popout | [http://purl.imsglobal.org/vocab/caliper/v1/action#OpenedPopout](http://purl.imsglobal.org/vocab/caliper/v1/action#OpenedPopout) | |
| <a name="paused" />paused | [http://purl.imsglobal.org/vocab/caliper/v1/action#Paused](http://purl.imsglobal.org/vocab/caliper/v1/action#Paused) | |
| <a name="posted" />posted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Posted](http://purl.imsglobal.org/vocab/caliper/v1/action#Posted) | [to cause to be directed or transmitted to another place](http://wordnet-rdf.princeton.edu/wn31/201033289-v)  |
| <a name="questioned" />questioned | [http://purl.imsglobal.org/vocab/caliper/v1/action#Questioned](http://purl.imsglobal.org/vocab/caliper/v1/action#Questioned) | |
| <a name="ranked" />ranked | [http://purl.imsglobal.org/vocab/caliper/v1/action#Ranked](http://purl.imsglobal.org/vocab/caliper/v1/action#Ranked) | |
| <a name="recommended" />recommended | [http://purl.imsglobal.org/vocab/caliper/v1/action#Recommended](http://purl.imsglobal.org/vocab/caliper/v1/action#Recommended) | |
| <a name="removed" />removed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Removed](http://purl.imsglobal.org/vocab/caliper/v1/action#Removed) | [remove from sight](http://wordnet-rdf.princeton.edu/wn31/200181704-v) |
| <a name="reset" />reset | [http://purl.imsglobal.org/vocab/caliper/v1/action#Reset](http://purl.imsglobal.org/vocab/caliper/v1/action#Reset) | [set anew](http://wordnet-rdf.princeton.edu/wn31/200949623-v) |
| <a name="restarted" />restarted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Restarted](http://purl.imsglobal.org/vocab/caliper/v1/action#Restarted) | |
| <a name="resumed" />resumed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Resumed](http://purl.imsglobal.org/vocab/caliper/v1/action#Resumed) | |
| <a name="retrieved" />retrieved | [http://purl.imsglobal.org/vocab/caliper/v1/action#Retrieved](http://purl.imsglobal.org/vocab/caliper/v1/action#Retrieved) | [obtain or retrieve from a storage device; as of information on a computer](http://wordnet-rdf.princeton.edu/wn31/202253616-v) |
| <a name="reviewed" />reviewed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Reviewed](http://purl.imsglobal.org/vocab/caliper/v1/action#Reviewed) | |
| <a name="rewound" />rewound | [http://purl.imsglobal.org/vocab/caliper/v1/action#Rewound](http://purl.imsglobal.org/vocab/caliper/v1/action#Rewound) | |
| <a name="searched" />searched | [http://purl.imsglobal.org/vocab/caliper/v1/action#Searched](http://purl.imsglobal.org/vocab/caliper/v1/action#Searched) | |
| <a name="shared" />shared | [http://purl.imsglobal.org/vocab/caliper/v1/action#Shared](http://purl.imsglobal.org/vocab/caliper/v1/action#Shared) | |
| <a name="showed" />showed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Showed](http://purl.imsglobal.org/vocab/caliper/v1/action#Showed) | |
| <a name="skipped" />skipped | [http://purl.imsglobal.org/vocab/caliper/v1/action#Skipped](http://purl.imsglobal.org/vocab/caliper/v1/action#Skipped) | |
| <a name="started" />started | [http://purl.imsglobal.org/vocab/caliper/v1/action#Started](http://purl.imsglobal.org/vocab/caliper/v1/action#Started) | |
| <a name="submitted" />submitted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Submitted](http://purl.imsglobal.org/vocab/caliper/v1/action#Submitted) | |
| <a name="subscribed" />subscribed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed) | [ receive or obtain regularly](http://wordnet-rdf.princeton.edu/wn31/202214527-v) |
| <a name="tagged" />tagged | [http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged](http://purl.imsglobal.org/vocab/caliper/v1/action#Tagged) | |
| <a name="timedOut" />timed out | [http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut](http://purl.imsglobal.org/vocab/caliper/v1/action#TimedOut) | |
| <a name="unmuted" />unmuted | [http://purl.imsglobal.org/vocab/caliper/v1/action#Unmuted](http://purl.imsglobal.org/vocab/caliper/v1/action#Unmuted) | inverse of muted |
| <a name="unsubscribed" />unsubscribed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed](http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed) | inverse of subscribed |
| <a name="viewed" />viewed | [http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed](http://purl.imsglobal.org/vocab/caliper/v1/action#Viewed) |[look at carefully; study mentally](http://wordnet-rdf.princeton.edu/wn31/202134765-v) |

<a name="entities" />
## 7.0 Entities

TODO: OVERVIEW

<a name="entity" />
### 7.1 Entity
A Caliper Entity is a generic class that is analogous to an [sdo:Thing](http://schema.org/Thing).  Entity is a generic type that is subclassed for greater type specificity.  Given that Entity represents a generic type it is RECOMMENDED that only subclasses of Entity be employed to represent nodes in the learning graph.

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
[Agent](#agent), [Annotation](#annotation), [Assessment](#assessment), [AssessmentItem](#assessmentItem), [AssignableDigitalResource](#assignableDigitalResource), [Attempt](#attempt), [AudioObject](#audioobject), [BookmarkAnnotation](#bookmarkAnnotation), [Chapter](#chapter), [Collection](#collection), [CourseOffering](#courseOffering), [CourseSection](#courseSection), [DigitalResource](#digitalResource), [Document](#document), [EpubChapter](#epubChapter), [EpubPart](#epubPart), [EpubSubChapter](#epubSubChapter), [EpubVolume](#epubVolume), [FillinBlankResponse](#fillinBlankResponse), [Frame](#frame), [Forum](#forum), [Group](#group), [HighlightAnnotation](#highlightAnnotation), [ImageObject](#imageobject), [LearningObjective](#learningObjective), [MediaLocation](#mediaLocation), [MediaObject](#mediaobject), [Membership](#membership), [Message](#message), [MultipleChoiceResponse](#multipleChoiceResponse), [MultipleResponseResponse](#multipleResponseResponse), [Organization](#organization), [Page](#page), [Person](#person), [Reading](#reading), [Response](#response), [Result](#result), [SelectTextResponse](#selectTextResponse), [Session](#session), [SharedAnnotation](#sharedAnnotation), [SoftwareApplication](#softwareapplication), [TagAnnotation](#tagAnnotation), [Thread](#thread), [TrueFalseResponse](#trueFalseResponse), [VideoObject](#videoobject), [WebPage](#webpage)

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
| Anthony Whyte [arwhyte](http://github.com/arwhyte) | University of Michigan |
| Viktor Haag [ViktorHaag](https://github.com/ViktorHaag) | DTL |

TODO: ADD OTHERS

<a name="appendixA" />
## Appendix A: Caliper Entities

<a name="agent" />
### Agent
A Caliper Agent is a generic class that represents an Entity that can initiate or perform an action.  It is analogous to a [foaf:Agent](http://xmlns.com/foaf/spec/#term_Agent).  Agent inherits all the properties and requirements defined for [Entity](#entity), its superclass.  Given that Agent represents a generic type it is RECOMMENDED that only subclasses of Agent be employed to represent nodes in the learning graph.

#### subClassOf
[Entity](#entity)

#### Subclasses 
[Organization](#organization), [Person](#person), [SoftwareApplication](#softwareapplication)

### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | An Agent SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, an Agent MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | If a generic Agent is created instead of one of its subclasses, the value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Agent; otherwise the value MUST be assigned the IRI appropriate for the subclass, e.g., http://purl.imsglobal.org/caliper/v1/Person. |

#### Optional properties
Inherited from [Entity](#entity).

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/tokens/bu435gy9z2Np41sV",
    "@type": "http://purl.imsglobal.org/caliper/v1/Agent"
}
```

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

###### Example
```json
{
    TODO
}
```

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
    "@id": "https://example.edu/semesters/201601/courses/301/assessments/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Assessment",
    "name": "Quiz One",
    "items": [
        {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/1",
            "@type": "http: //purl.imsglobal.org/caliper/v1/AssessmentItem"
        },
        {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/2",
            "@type": "http: //purl.imsglobal.org/caliper/v1/AssessmentItem"
        },
        {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/3",
            "@type": "http: //purl.imsglobal.org/caliper/v1/AssessmentItem"
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
    "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/3",
    "@type": "http: //purl.imsglobal.org/caliper/v1/AssessmentItem",
    "isPartOf": {
        "@id": "https://example.edu/semesters/201601/courses/301/assessments/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
    },
    "dateCreated": "2016-08-01T06:00:00.000Z",
    "datePublished": "2016-08-15T09:30:00.000Z",
    "maxAttempts": 2,
    "maxScore": 5,
    "maxSubmits": 2,
    "extensions": {
        "itemType": "true/false",
        "itemText": "Is a Python tuple mutable?",
        "itemCorrectResponse": "false",
        "itemIncorrectResponse": "true"
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

###### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/semesters/201601/courses/301/assign/2",
    "@type": "http: //purl.imsglobal.org/caliper/v1/AssignableDigitalResource",
    "name": "Week 2 Reflection",
    "description": "3-5 page reflection on week's assigned readings.",
    "dateCreated": "2016-09-01T06:00:00.000Z",
    "dateToStartOn": "2016-09-15T11:59:59.000Z",
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
| actor | [Person](#person) | The Person who initiated the Attempt MUST be specified. |
| assignable | [DigitalResource](#digitalResource) | The DigitalResource that constitutes the object of the assignment MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |
| count | [xsd:nonNegativeInteger](https://www.w3.org/TR/xmlschema11-2/#nonNegativeInteger) | The total number of attempts inclusive of the current Attempt that have been registered against the assigned DigitalResource. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Attempt includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | Represents when this Attempt commenced.  A start time SHOULD be provided.  If a start time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | Represents when this Attempt ended or was terminated.  For a [completed](#completed) or [submitted](#submitted) action an end time SHOULD be provided.  If an end time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) |Represents the total interval of time required to complete this Attempt.  If a duration is specified the value MUST conform to the ISO-8601 duration format. |

#### Example
```json
{
    "@id": "https://example.edu/semesters/201601/courses/301/assess/1/users/554433/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "assignable": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Assessment"
    },
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http://purl.imsglobal.org/caliper/v1/Person"
    },
    "count": 1,
    "dateCreated": "2016-09-15T10:05:00.000Z",
    "startedAtTime": "2016-09-15T10:05:00.000Z",
    "endedAtTime": "2016-09-15T10:55:30.000Z",
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
  "@id": "http://www.fdrlibrary.marist.edu/archives/collections/utterances_audio/direct_download.php?file=afdr067.mp3",
  "@type": "http://purl.imsglobal.org/caliper/v1/AudioObject",
  "name": "Franklin D. Roosevelt. Madison Square Garden Speech (31 October 1936)",
  "duration": "PT36M55S"
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
| actor | [Person](#person) | The Person who created the BookmarkAnnotation MUST be specified. |
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
  "@id": "https://example.com/bookmarks/813cb2c6-75ec-410f-8dab-ef047afb92e5",
  "@type": "http://purl.imsglobal.org/caliper/v1/BookmarkAnnotation",
  "annotated": "https://example.com/viewer/book/34843#epubcfi(/4/3/2)",
  "bookmarkNotes": "The Intolerable Acts (1774)--bad idea Lord North",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
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
    TODO
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
    "@id": "https://example.edu/semesters/201601/courses/301/sections/1/groups",
    "@type": "http://purl.imsglobal.org/caliper/v1/Collection",
    "name": "Groups",
    "items": [
        {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1/groups/1",
            "@type": "http: //purl.imsglobal.org/caliper/v1/Group"
        },
        {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1/groups/3",
            "@type": "http: //purl.imsglobal.org/caliper/v1/Group"
        },
        {
            "@id": "https://example.edu/semesters/201601/courses/301/sections/1/groups/5",
            "@type": "http: //purl.imsglobal.org/caliper/v1/Group"
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
    "@id": "https: //example.edu/semesters/201601/courses/1776",
    "@type": "http: //purl.imsglobal.org/caliper/v1/CourseOffering",
    "courseNumber": "POL101",
    "academicSession": "Fall-2016",
    "name": "Political Science 101: The American Revolution",
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "dateModified": "2015-09-02T11:30:00.000Z"
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
    "@id": "https: //example.edu/semesters/201601/courses/1776/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "academicSession": "Fall-2016",
    "courseNumber": "POL101-1",
    "name": "American Revolution 101",
    "category": "lecture",
    "subOrganizationOf": {
        "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
        "@id": "https: //example.edu/semesters/201601/courses/1776",
        "@type": "http: //purl.imsglobal.org/caliper/v1/CourseOffering",
        "courseNumber": "POL101"
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
| alignedLearningObjective | List&lt;[LearningObjective](#learningobjective)&gt; | One or more [LearningObjectives](#learningobject) that describe what the actor is expected to accomplish after engaging with this DigitalResource. |
| isPartOf | [DigitalResource](#digitalResource) | A related DigitalResource that includes or incorporates this DigitalResource as a part of its whole.  Analogous to [sdo:isPartOf](http://schema.org/isPartOf) or [dcterms:isPartOf](http://purl.org/dc/terms/isPartOf). |
| datePublished | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | Represents the publication date of this DigitalResource.  If a publication date is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [sdo:datePublished](http://schema.org/datePublished) |
| version | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) | An identifier that designates the current form of this DigitalResource.  Analogous to [sdo:version](http://schema.org/version) |

#### Deprecated properties
The following properties have been deprecated and will be removed in a future version of the specification.  Deprecated properties SHOULD NOT be referenced.

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| objectType | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) |  DEPRECATED |

###### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https: //example.edu/semesters/201601/courses/1776/sections/3/resources/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/DigitalResource",
    "name": "Course Syllabus",
    "creators": [
        {
            "@id": "https://example.edu/users/223344",
            "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        }
    ],
    "isPartOf": {
        "@id": "https: //example.edu/semesters/201601/courses/1776/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection"
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
    "@id": "https://example.edu/semesters/201601/courses/301/sections/1/collections/3",
    "@type": "http://purl.imsglobal.org/caliper/v1/Collection",
    "name": "Video Collection",
    "items": [
        {
            "@id": "https://example.com/videos/1225",
            "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
            "mediaType": "video/ogg",
            "name": "Video 1225",
            "dateCreated": "2016-08-01T06:00:00.000Z",
            "duration": "PT1H12M27S",
            "version": "1.0"
        },
        {
            "@id": "https://example.com/videos/5629",
            "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
            "mediaType": "video/ogg",
            "name": "Video 5629",
            "dateCreated": "2016-08-01T06:00:00.000Z",
            "duration": "PT55M13S",
            "version": "2.1"
        }
    ],
    "isPartOf": {
        "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
        "subOrganizationOf": {
            "@id": "https://example.edu/semesters/201601/courses/301",
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
    TODO
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3/1/1)",
    "@type": "http://purl.imsglobal.org/caliper/v1/EpubChapter",
    "name": "Caliper EpubChapter Deprecation",
    "isPartOf": {
        "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3/1)",
        "@type": "http://purl.imsglobal.org/caliper/v1/EpubPart",
        "name": "Caliper Entity Deprecations",
        "isPartof": {
            "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3)",
            "@type": "http://purl.imsglobal.org/caliper/v1/EpubVolume",
            "name": "Caliper Deprecations",
            "version": "1.1"
        }
    }
}
```

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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3/1)",
    "@type": "http://purl.imsglobal.org/caliper/v1/EpubPart",
    "name": "Caliper Entity Deprecations",
    "isPartof": {
        "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3)",
        "@type": "http://purl.imsglobal.org/caliper/v1/EpubVolume",
        "name": "Caliper Deprecations",
        "version": "1.1"
    }
}
```

<a name="epubSubChapter" />
#### EpubSubChapter (DEPRECATED)
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

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3/1/1/1)",
    "@type": "http://purl.imsglobal.org/caliper/v1/EpubSubChapter",
    "name": "Caliper EpubSubChapter Deprecation",
    "isPartOf": {
        "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3/1/1)",
        "@type": "http://purl.imsglobal.org/caliper/v1/EpubChapter",
        "name": "Caliper EpubChapter Deprecation",
        "isPartOf": {
            "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3/1)",
            "@type": "http://purl.imsglobal.org/caliper/v1/EpubPart",
            "name": "Caliper Entity Deprecations",
            "isPartof": {
                "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3)",
                "@type": "http://purl.imsglobal.org/caliper/v1/EpubVolume",
                "name": "Caliper Deprecations",
                "version": "1.1"
            }
        }
    }
}
```

<a name="epubVolume" />
#### EpubVolume (DEPRECATED)
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

#### Example
```json
{
    "@id": "https://example.com/viewer/book/34843#epubcfi(/4/3)",
    "@type": "http://purl.imsglobal.org/caliper/v1/EpubVolume",
    "name": "Caliper Deprecations",
    "version": "1.1"
}
```

<a name="fillinBlankResponse" />
### FillinBlankResponse
A Caliper FillinBlankResponse represents a form of response in which a respondent is asked to provide one or more words, expressions or short phrases that correctly completes a statement.  FillinBlankResponse inherits all the properties and requirements defined for [Response](#response), its superclass.

TODO
* confirm: eliminate actor and assignable in favor of attempt in order to eliminate unnecessary redundancy.

#### subClassOf 
[Response](#response)

#### Required properties
| Property | Type | Requirements |
| -------- | ----- | -------------- |
| context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/ctx/caliper/v1/Context.  The context MAY be omitted if it duplicates the enclosing Event context. |
| id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A FillinBlankResponse SHOULD be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that Entity data can be linked and shared.  In cases where an IRI is inappropriate, a FillinBlankResponse MUST be assigned a blank node identifier. |
| type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The value MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/FillinBlankResponse. |
| actor | [Person](#person) | The Person who initiated the Response MUST be specified. |
| assignable | [DigitalResource](#digitalResource) | The DigitalResource that constitutes the object of the assignment MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Response includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| value | List&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt; | The ordered set of one or more words, expressions or short phrases that constitutes the response MAY be provided.  |

#### Example
```json
{
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/1/users/554433/responses/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
    "actor": {
        "@id": "https://example.edu/user/554433",
        "@type": "http: //purl.imsglobal.org/caliper/v1/Person"
    },
    "assignable": {
        "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
        "isPartOf": {
            "@id": "https: //example.edu/semesters/201601/courses/301/assess/1",
            "@type": "http: //purl.imsglobal.org/caliper/v1/Assessment"
        }
    },
    "attempt": {
        "@id": "https: //example.edu/terms/2/courses/215/sections/3/assess/1/items/1/users/554433/attempts/1",
        "@type": "http: //purl.imsglobal.org/caliper/v1/Attempt",
        "actor": {
            "@id": "https://example.edu/user/554433",
            "@type": "http: //purl.imsglobal.org/caliper/v1/Person"
        },
        "assignable": {
            "@id": "https://example.edu/semesters/201601/courses/301/assess/1/items/1",
            "@type": "http://purl.imsglobal.org/caliper/v1/AssessmentItem",
            "isPartOf": {
                "@id": "https: //example.edu/semesters/201601/courses/301/assess/1",
                "@type": "http: //purl.imsglobal.org/caliper/v1/Assessment"
            }
        },
        "count": 1,
        "dateCreated": "2015-08-01T06:00:00.000Z",
        "startedAtTime": "2015-09-15T10:15:00.000Z",
        "endedAtTime": "2015-09-15T10:15:15.000Z"
    },
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "startedAtTime": "2015-09-15T10:15:00.000Z",
    "endedAtTime": "2015-09-15T10:15:15.000Z",
    "values": [ "tuple", "immutable" ]
}
```

<a name="frame" />
#### Frame

TODO

###### Example
```
{

 TODO
 
}
```

<a name="forum" />
#### Forum
A Caliper ```Forum``` is a channel or virtual space in which group discussions take place.  A ```Forum``` typically comprises one or more threaded discussions to which members can subscribe, post messages and reply to other messages.  It is analogous to a [sioc:Forum](http://rfds.org/sioc/spec/#term_Forum).

###### subClassOf 
[Collection](#collection)

###### &#64;type 
[http://purl.imsglobal.org/caliper/v1/Forum](http://purl.imsglobal.org/caliper/v1/Forum)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| items | List&lt;[Thread](#thread)&gt; | The set of ```items``` that comprise this ```Forum```. | 0..1 |

###### Requirements
* A ```Forum``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Forum.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/semesters/201601/courses/301/forums/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
  "name": "Caliper Forum",
  "items": [
    {
      "@id": "https://example.edu/semesters/201601/courses/301/forums/1/topics/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "name": "Caliper Information Model",
      "dateCreated": "2016-09-01T09:30:00.000Z"
    },
    {
      "@id": "https://example.edu/semesters/201601/courses/301/forums/1/topics/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "name": "Caliper Sensor API",
      "dateCreated": "2016-09-01T09:30:00.000Z"
    },
    {
      "@id": "https://example.edu/semesters/201601/courses/301/forums/1/topics/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
      "name": "Caliper Certification",
      "dateCreated": "2016-09-01T09:30:00.000Z"
    }
  ],
  "isPartOf": {
    "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
    "subOrganizationOf": {
      "@id": "https://example.edu/semesters/201601/courses/301",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering"
    }
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="group" />
#### Group

TODO

###### Example
```
{

 TODO
 
}
```

<a name="highlightAnnotation" />
#### HighlightAnnotation
A Caliper ```HighlightAnnotation``` represents the act of marking a particular segment of a  ```DigitalResource``` . . . . TODO

###### subClassOf
Annotation](#annotation)

###### &#64;type
[http://purl.imsglobal.org/caliper/v1/HighlightAnnotation](http://purl.imsglobal.org/caliper/v1/HighlightAnnotation)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| selection | [TextPositionSelector](#textPositionSelector) | The range of highlighted text based on its ```start``` and ```end``` positions.  | 0..1 |
| selectionText | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)  | The highlighted segment or fragment of the annotated ```DigitalResource```. | 0..1 |

###### Requirements
* A ```HighlightAnnotation``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/HighlightAnnotation.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/highlights/12345",
  "@type": "http://purl.imsglobal.org/caliper/v1/HighlightAnnotation",
  "annotated": "https://example.com/viewer/book/34843#epubcfi(/4/3/1)",
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "dateModified": "2015-09-02T11:30:00.000Z",
  "selection": {
    "end": "489",
    "start": "455"
  },
  "selectionText": "Life, Liberty and the pursuit of Happiness"
}
```

<a name="imageObject" />
#### ImageObject

A Caliper ```ImageObject``` represents an image file.  It is analogous to [sdo:ImageObject](http://schema.org/ImageObject).

###### subClassOf 
[MediaObject](#mediaObject)

###### &#64;type 
[http://purl.imsglobal.org/caliper/v1/ImageObject](http://purl.imsglobal.org/caliper/v1/ImageObject)

###### Requirements
* An ```ImageObject``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/ImageObject.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://upload.wikimedia.org/wikipedia/commons/c/c5/Jesse_Owens3.jpg",
  "@type": "http://purl.imsglobal.org/caliper/v1/ImageObject",
  "name": "Jesse Owens"
}
```

<a name="learningObjective" />
#### LearningObjective

TODO

###### Example
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
      "dateCreated": "2016-08-01T06:00:00.000Z"
    }
  ],
  "duration": "PT50M30S",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z",
  "version": "1.0"
}
```

<a name="mediaLocation" />
#### MediaLocation

TODO

###### Example
```
{

 TODO
 
}
```

<a name="mediaObject" />
#### MediaObject
A Caliper ```MediaObject``` represents a generic piece of media content analogous to [sdo:MediaObject](http://schema.org/MediaObject).

###### subClassOf 
[DigitalResource](#digitalResource)

###### &#64;type 
[http://purl.imsglobal.org/caliper/v1/MediaObject](http://purl.imsglobal.org/caliper/v1/MediaObject)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| duration | [xsd:string](https://www.w3.org/TR/xmlschema11-2/#string) | The length of time to completion.  Analogous to [sdo:duration](http://schema.org/duration).  | 0..1 |

###### Requirements
* Given that ```MediaObject``` represents a generic type it is RECOMMENDED that only its subclasses be employed to represent nodes in the learning graph.
* If a generic ```MediaObject``` is included in an [Event](#event) instead of one of its subclasses, the ```MediaObject``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MediaObject.
* If a ```duration``` is specified the value MUST conform to the ISO-8601 duration format.

###### Subclasses
[AudioObject](#audioObject.md), [ImageObject](#imageObject.md), [VideoObject](#videoObject) 

<a name="membership" />
#### Membership

TODO

###### Example
```
{

 TODO
 
}
```

<a name="message" />
#### Message
A Caliper ```Message``` is a digital form of written communication sent to a recipient. A series of ```Messages``` may constitute a [Thread](#thread) if they share a common subject and are connected by a reply or by date relationships. It is analogous to an [sioc:Post](http://rfds.org/sioc/spec/#term_Post).

###### subClassOf 
[DigitalResource](#digitalResource)

###### &#64;type 
[http://purl.imsglobal.org/caliper/v1/Message](http://purl.imsglobal.org/caliper/v1/Message)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ---: |
| creator | [Agent](#agent) | The author or originator of this ```Message```, typically a [Person](#person).  Analogous to [sioc:has_creator](http://rdfs.org/sioc/spec/#term_has_creator) or [sdo:creator](http://schema.org/creator). | 0..1|
| replyTo | [Message](#message) | The prior ```Message```, if any, that prompted the posting of this ```Message``` in the form of a reply or response.  Analogous to [sioc:reply_of](http://rdfs.org/sioc/spec/#term_reply_of). | 0..1 |
| isPartOf | [Thread](#thread) | The ```Thread``` of which this Message forms a part.  Analogous to [sioc:has_creator](http://rdfs.org/sioc/spec/#term_has_creator). | 0..1 |
| ~~content~~ | ~~[xsd:string](https://www.w3.org/TR/xmlschema11-2/#string)~~ | ~~Plain-text rendering of the content of the ```Message```.  Analogous to [sioc:content](http://rdfs.org/sioc/spec/#content). ~~ | ~~ 0..1 ~~ |
| attachments | List&lt;[DigitalResource](#digitalResource)&gt; | A set of one or more items attached to this ```Message```.  Analogous to [sioc:attachment](http://rdfs.org/sioc/spec/#term_attachment). | 0..1 |

###### Requirements
* A ```Message``` SHOULD specify a [creator](#creator).
* A ```Message``` SHOULD specify a [replyTo](#replyTo) if the ```Message``` represents a response to a previously posted ```Message```.

###### JSON-LD Serialization
* A ```Message``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Message.
* A ```Message``` @id property SHOULD be assigned an IRI; otherwise a [blank node](#blankNode) identifier.

##### Example: MessageEvent.object posted
```
{
     "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/2",
     "@type": "http://purl.imsglobal.org/caliper/v1/Message",
     "creators": [
         {
             "@id": "https://example.edu/users/554433",
             "@type": "http://purl.imsglobal.org/caliper/v1/Person"
         }
     ],
     "isPartOf": {
         "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1",
         "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
         "name": "Caliper Adoption",
         "isPartOf": {
             "@id": "https://example.edu/semesters/201601/courses/301/forums/2",
             "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
             "name": "Caliper Forum"
         }
     },
     "dateCreated": "2016-09-15T10:15:00.000Z"
 }
 ```
##### Example: Message Reply
```
{
    "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/3",
    "@type": "http://purl.imsglobal.org/caliper/v1/Message",
    "creators": [
        {
             "@id": "https://example.edu/users/778899",
             "@type": "http://purl.imsglobal.org/caliper/v1/Person"
        }
     ],
     "replyTo": {
         "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/2",
         "@type": "http://purl.imsglobal.org/caliper/v1/Message"
     },
     "isPartOf": {
         "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1",
         "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
         "isPartOf": {
             "@id": "https://example.edu/semesters/201601/courses/301/forums/2",
             "@type": "http://purl.imsglobal.org/caliper/v1/Forum"
         }
     },
     "dateCreated": "2016-09-15T10:15:30.000Z"
 }
 ```
<a name="multipleChoiceResponse" />
#### MultipleChoiceResponse
A Caliper ```MultipleChoiceResponse``` represents a form of response in which a respondent is asked to provide the best possible answer from a list of choices.

###### subClassOf 
[Response](#response)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| value | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | The selected choice.  | 0..1 |

###### JSON-LD Serialization
* A ```MultipleChoiceResponse``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MultipleChoiceResponse.
* A ```MultipleChoiceResponse``` [@id](#id) property SHOULD be assigned an IRI; otherwise a [blank node](#blankNode) identifier.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/2/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
  "actor": "https://example.edu/user/554433",
  "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/2",
  "attempt": {
    "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/2/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": "https://example.edu/user/554433",
    "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/2",
    "count": 1,
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "startedAtTime": "2015-09-15T10:15:00.000Z"
  },
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "startedAtTime": "2015-09-15T10:15:00.000Z",
  "value": "C"
}
```

<a name="multipleResponseResponse" />
#### MultipleResponseResponse
A Caliper ```MultipleResponseResponse``` represents a form of response in which a respondent is asked to select more than one correct answer from a list of choices.

###### subClassOf 
[Response](#response)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| values | String array | One or more response values  | 0..1 |

###### JSON-LD Serialization
* A ```MultipleResponseResponse``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/MultipleResponseResponse.
* A ```MultipleResponseResponse``` [@id](#id) property SHOULD be assigned an IRI; otherwise a [blank node](#blankNode) identifier.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/3/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
  "actor": "https://example.edu/user/554433",
  "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/3",
  "attempt": {
    "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/3/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": "https://example.edu/user/554433",
    "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/3",
    "count": 1,
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "startedAtTime": "2015-09-15T10:15:00.000Z"
  },
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "startedAtTime": "2015-09-15T10:15:00.000Z",
  "values": ["A", "D"]
}
```

<a name="organization" />
#### Organization
A Caliper ```Organization``` represents a group of people organized into a community or other social, commercial, educational or political structure.  The group has a common purpose or reason for existence that spans beyond the set of people belonging to it and can act as an [Agent](#agent). An ```Organization``` can often be decomposed into a hierarchical structure.  It is analogous to a [w3c:Organization](https://www.w3.org/TR/vocab-org/#class-organization).

###### subClassOf
[Agent](#agent)

###### &#64;type
[http://purl.imsglobal.org/caliper/v1/Organization](http://purl.imsglobal.org/caliper/v1/Organization)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- |---: |
| subOrganizationOf | [Organization](#organization) | The parent ```Organization``` of this ```Organization```. | 0..1 |

###### Requirements
* An ```Organization``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Organization.

###### Subclasses
[Group](#group)

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/colleges/1/departments/2",
  "@type": "http://purl.imsglobal.org/caliper/v1/Organization",
  "name": "Department of History",
  "subOrganizationOf": {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/colleges/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Organization",
    "name": "College of Social Science"
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
    TODO
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
    "dateCreated": "2016-08-01T06:00:00.000Z"
}
```

<a name="reading" />
#### Reading (DEPRECATED)
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

#### Example
```json
{
    TODO
}
```

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
| actor | [Person](#person) | The Person who initiated the Response MUST be specified. |
| assignable | [DigitalResource](#digitalResource) | The DigitalResource that constitutes the object of the assignment MUST be specified.  Note that DigitalResource is a generic type that is subclassed for greater type specificity.  Utilize DigitalResource only if no suitable subclass exists to represent the object. |

#### Optional properties
In addition to properties inherited from [Entity](#entity), Response includes the following additional optional properties:

| Property | Type | Requirements |
| -------- | ----- | -------------- |
| attempt| [Attempt](#attempt) | The Attempt associated with this Response SHOULD BE referenced. |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | Represents when this Response commenced.  A start time SHOULD be provided.  If a start time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | Represents when this Response was completed or ended.  An end time SHOULD be provided.  If an end time is specified the value MUST conform to the ISO-8601 format for date and time with millisecond precision.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) |Represents the total interval of time required to complete this Response.  If a duration is specified the value MUST conform to the ISO-8601 duration format. |

#### Example
```json
{
    TODO
}
```

<a name="result" />
#### Result

TODO

###### Example
```
{

 TODO
 
}
```

<a name="selectTextResponse" />
#### SelectTextResponse
A Caliper ```SelectTextResponse``` represents a response that identifies text or a mapping from a presented paragraph or list.

###### subClassOf 
[Response](#response)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| values | String array | One or more response values  | 0..1 |

###### JSON-LD Serialization
* A ```SelectTextResponse``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SelectTextResponse.
* A ```SelectTextResponse``` [@id](#id) property SHOULD be assigned an IRI; otherwise a [blank node](#blankNode) identifier.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/4/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
  "actor": "https://example.edu/user/554433",
  "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/4",
  "attempt": {
    "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/4/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": "https://example.edu/user/554433",
    "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/4",
    "count": 1,
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "startedAtTime": "2015-09-15T10:15:00.000Z"
  },
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "startedAtTime": "2015-09-15T10:15:00.000Z",
  "values": ["You are quite right in calling for negotiation. Indeed, this is the very purpose of direct action. Nonviolent direct action seeks to create such a crisis and foster such a tension that a community which has constantly refused to negotiate is forced to confront the issue. It seeks so to dramatize the issue that it can no longer be ignored."]
}
```

<a name="session" />
#### Session
A Caliper ```Session``` represents a Web application user session.

###### subClassOf
[Entity](#entity)

###### &#64;type
[http://purl.imsglobal.org/caliper/v1/Session](http://purl.imsglobal.org/caliper/v1/Session)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ---: |
| actor | [Agent](#agent) | The ```Agent``` who establishes this ```Session```.| 0..1 |
| startedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when a ```Session``` commenced.  Analogous to [provo:startedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#startedAtTime). | 0..1 |
| endedAtTime | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted date and time expressed with millisecond precision that represents when a ```Session``` ended or was terminated.  Analogous to [provo:endedAtTime](https://www.w3.org/TR/2013/REC-prov-o-20130430/#endedAtTime). | 0..1 |
| duration | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | ISO 8601 formatted total interval of time required to complete this ```Session```. | 0..1 |

###### Requirements
* A ```Session``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Session.
* It is RECOMMENDED that a Session [actor](#actor) be specified.
* If a ```Session``` [startedAtTime](#startedAtTime) is specified the value MUST conform to the ISO-8601 date and time format with millisecond precision.  
* If a ```Session``` [endedAtTime](#endedAtTime) is specified the value MUST conform to the ISO-8601 date and time format with millisecond precision.
* If a ```Session``` [duration](#duration) is specified the value MUST conform to the ISO-8601 duration format.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/viewer/session-123456789",
  "@type": "http://purl.imsglobal.org/caliper/v1/Session",
  "name": "session-123456789",
  "actor": {
    "@id": "https://example.edu/user/554433",
    "@type": "http://purl.imsglobal.org/caliper/v1/Person",
    "dateCreated": "2016-08-01T06:00:00.000Z"
  },
  "dateCreated": "2016-09-15T10:15:00.000Z",
  "startedAtTime": "2016-09-15T10:15:00.000Z"
}
```

<a name="sharedAnnotation" />
#### SharedAnnotation
A Caliper ```SharedAnnotation``` represents the act of sharing a reference to a ```DigitalResource``` with other agents.

###### subClassOf
Annotation](#annotation)

###### &#64;type
[http://purl.imsglobal.org/caliper/v1/SharedAnnotation](http://purl.imsglobal.org/caliper/v1/SharedAnnotation)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| withAgents | List&lt;[Agent](#agent)&gt; | The set of one or more agents with whom a ```DigitalResource``` is shared. | 0..1 |

###### Requirements
* A ```SharedAnnotation``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SharedAnnotation.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/shared/9999",
  "@type": "http://purl.imsglobal.org/caliper/v1/SharedAnnotation",
  "annotated": "https://example.com/viewer/book/34843#epubcfi(/4/3/3)",
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "dateModified": "2015-09-02T11:30:00.000Z",
  "withAgents": [
    {
      "@id": "https://example.edu/user/657585",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person",
      "dateCreated": "2015-08-01T06:00:00.000Z",
      "dateModified": "2015-09-02T11:30:00.000Z"
    },
    {
      "@id": "https://example.edu/user/667788",
      "@type": "http://purl.imsglobal.org/caliper/v1/Person",
      "dateCreated": "2015-08-01T06:00:00.000Z",
      "dateModified": "2015-09-02T11:30:00.000Z"
    }
  ]
}
```

<a name="softwareapplication" />
#### SoftwareApplication
A Caliper ```SoftwareApplication``` represents a computer program, application, module, platform or system.  It is analogous to a [sdo:SoftwareApplication](http://schema.org/SoftwareApplication) or [dcmitype:Software](http://purl.org/dc/dcmitype/Software).

###### subClassOf
[Agent](#agent)

###### &#64;type
[http://purl.imsglobal.org/caliper/v1/SoftwareApplication](http://purl.imsglobal.org/caliper/v1/SoftwareApplication)

###### Requirements
* A ```SoftwareApplication``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/SoftwareApplication.

###### Example
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
A Caliper ```TagAnnotation``` represents the act of tagging a ```DigitalResource``` with . . . . TODO

###### subClassOf
Annotation](#annotation)

###### &#64;type
[http://purl.imsglobal.org/caliper/v1/TagAnnotation](http://purl.imsglobal.org/caliper/v1/TagAnnotation)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| tags | List&lt;[xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)&gt; | The set of one or more tags associated with the annotated ```DigitalResource```. | 0..1 |

###### Requirements
* A ```TagAnnotation``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/TagAnnotation.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/tags/7654",
  "@type": "http://purl.imsglobal.org/caliper/v1/TagAnnotation",
  "annotated": "https://example.com/viewer/book/34843#epubcfi(/4/3/4)",
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "dateModified": "2015-09-02T11:30:00.000Z",
  "tags": ["to read", "1765", "shared with project team"]
}
```

<a name="thread" />
#### Thread
A Caliper ```Thread``` represents a series of one or more messages that share a common subject and are connected by a reply or by date relationships. It is analogous to a [sioc:Thread](http://rfds.org/sioc/spec/#term_Thread).

###### subClassOf 
[Collection](#collection)

###### &#64;type 
[http://purl.imsglobal.org/caliper/v1/Thread](http://purl.imsglobal.org/caliper/v1/Thread)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ---: |
| isChildOf | [Forum](#forum) | The parent ```Forum``` of this ```Thread```.  Analogous to [sioc:has_parent](http://rdfs.org/sioc/spec/#term_has_parent). | 0..1 |
| items | List&lt;[Message](#message)&gt; | The set of ```items``` that comprise this ```Thread```. | 0.1 |

###### Requirements
* A ```Thread``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/Thread.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/semesters/201601/courses/301/forums/1/topics/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/Thread",
  "name": "Caliper Information Model",
  "items": [
    {
      "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/Message"
    },
    {
      "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/2",
      "@type": "http://purl.imsglobal.org/caliper/v1/Message",
      "replyTo": {
        "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/1",
        "@type": "http://purl.imsglobal.org/caliper/v1/Message"
      }
    },
    {
      "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/3",
      "@type": "http://purl.imsglobal.org/caliper/v1/Message",
      "replyTo": {
        "@id": "https://example.edu/semesters/201601/courses/301/forums/2/topics/1/messages/2",
        "@type": "http://purl.imsglobal.org/caliper/v1/Message"
      }
    }
  ],
  "isPartOf": {
    "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
    "@id": "https://example.edu/semesters/201601/courses/301/forums/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Forum",
    "name": "Caliper Forum",
    "isPartOf": {
      "@id": "https://example.edu/semesters/201601/courses/301/sections/1",
      "@type": "http://purl.imsglobal.org/caliper/v1/CourseSection",
      "subOrganizationOf": {
        "@id": "https://example.edu/semesters/201601/courses/301",
        "@type": "http://purl.imsglobal.org/caliper/v1/CourseOffering"
      }
    },
    "dateCreated": "2016-08-01T06:00:00.000Z",
    "dateModified": "2016-09-02T11:30:00.000Z"
  },
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z"
}
```

<a name="trueFalseResponse" />
#### TrueFalseResponse
A Caliper ```TrueFalseResponse``` represents a response to a question in which only two possible options are provided: true or false.

###### subClassOf 
[Response](#response)

###### Properties
| Property | Type | Description ||
| -------- | ---- | ----------- | ----: |
| value | [xsd:boolean]( https://www.w3.org/TR/xmlschema11-2/#boolean) | Either a true or false value is provided.  | 0..1 |

###### JSON-LD Serialization
* A ```TrueFalseResponse``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/TrueFalseResponse.
* A ```TrueFalseResponse``` [@id](#id) property SHOULD be assigned an IRI; otherwise a [blank node](#blankNode) identifier.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/5/responses/1",
  "@type": "http://purl.imsglobal.org/caliper/v1/FillinBlankResponse",
  "actor": "https://example.edu/user/554433",
  "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/5",
  "attempt": {
    "@id": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/5/attempts/1",
    "@type": "http://purl.imsglobal.org/caliper/v1/Attempt",
    "actor": "https://example.edu/user/554433",
    "assignable": "https://example.edu/terms/2/courses/215/sections/3/assessments/1/items/5",
    "count": 1,
    "dateCreated": "2015-08-01T06:00:00.000Z",
    "startedAtTime": "2015-09-15T10:15:00.000Z"
  },
  "dateCreated": "2015-08-01T06:00:00.000Z",
  "startedAtTime": "2015-09-15T10:15:00.000Z",
  "value": false
}
```

<a name="videoObject" />
#### VideoObject
A Caliper ```VideoObject``` represents a visual recording stored in digital form. It is analogous to [sdo:VideoObject](http://schema.org/VideoObject).

###### subClassOf 
[MediaObject](#mediaobject)

###### &#64;type 
[http://purl.imsglobal.org/caliper/v1/VideoObject](http://purl.imsglobal.org/caliper/v1/VideoObject)

###### Requirements
* A ```VideoObject``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/VideoObject.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.com/super-media-tool/videos/1225",
  "@type": "http://purl.imsglobal.org/caliper/v1/VideoObject",
  "name": "American Revolution - Key Figures Video",
  "duration": "PT58M37S",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z",
  "version": "1.0"
}
```

<a name="webPage" />
#### WebPage
A Caliper ```WebPage``` represents a document suitable for display in a web browser.  It is analogous to a [sdo:WebPage](http://schema.org/WebPage).

###### subClassOf 
[DigitalResource](#digitalResource)

###### &#64;type 
[http://purl.imsglobal.org/caliper/v1/WebPage](http://purl.imsglobal.org/caliper/v1/WebPage)

###### Requirements
* A ```WebPage``` [@type](#type) property MUST be assigned the IRI http://purl.imsglobal.org/caliper/v1/WebPage.

###### Example
```
{
  "@context": "http://purl.imsglobal.org/ctx/caliper/v1/Context",
  "@id": "https://example.edu/politicalScience/2015/american-revolution-101/index.html",
  "@type": "http://purl.imsglobal.org/caliper/v1/WebPage",
  "name": "American Revolution 101 Landing Page",
  "dateCreated": "2016-08-01T06:00:00.000Z",
  "dateModified": "2016-09-02T11:30:00.000Z",
  "version": "1.0"
}
```

<a name="appendixB" />
## Appendix B.  Miscellaneous Classes

TODO

### TextPositionSelector

TODO

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