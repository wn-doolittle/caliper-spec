### Caliper Analytics<sup>TM</sup> Specification, version 1.0
### IMS Global Learning Consortium, Inc.

### Table of Contents
* 1.0. [Introduction](#introduction)
* 1.x. [Namespaces](#namespaces)
* 1.x. [Definitions](#definitions)
* X.0. [Event](#event)
* X.0. [Entity](#entity)
* X.0. [Profiles](#profiles)
* X.x. [Contributors](#contributors)
*	[Appendix A: Caliper Actions](#appendixA)
* [Appendix B: Caliper Entities](#appendixB)


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

<a name="event"/>

### X.0. Event

__Node type:__ [http://purl.imsglobal.org/caliper/v1/Event](http://purl.imsglobal.org/caliper/v1/Event)

__Comment:__ a Caliper [Event](#event) is a generic class that represents the interaction between an [actor](#actor) and an [object](#actor) at a specific moment in time within the bounds of a specified context. For enhanced specificity utilize the several subclasses of [Event](#event) when constructing a [Event](#event) rather than instantiating instances of the [Event](#event) class itself.

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

<a name="entity">

### X.0. Entity

__type__: [http://purl.imsglobal.org/caliper/v1/Entity](http://purl.imsglobal.org/caliper/v1/Entity)

__Comment__: a Caliper [Entity](#entity) is a generic class that is analogous to an [sdo:Thing](http://schema.org/Thing).  Given its generic nature it is *recommended* that only subclasses of [Entity](#entity) be employed to represent nodes in the learning graph.  

__Properties__

| Property | Type | Description ||
| -------- | ---- | ----------- | -----------: |
| @context | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD context represented by a globally-scoped IRI. | 1 |
| @id | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD identifier represented as a globally-scoped IRI or a locally-scoped blank node identifier. | 1 |
| @type | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | JSON-LD type represented as a globally-scoped IRI. | 1 |
| name | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A word or phrase by which the [Entity](#entity) is known.  Analogous to [sdo:name](http://schema.org/name) | 0..1 |
| description | [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string) | A short representation of the [Entity](#entity) in written form.  Analogous to [sdo:description](http://schema.org/description) | 0..1 |
| extensions | Map&lt;[xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string), [xsd:string]( https://www.w3.org/TR/xmlschema11-2/#string)&gt;   | A map of additional key/value properties relevant to the [Entity](#entity) | 0..1 |
| dateCreated | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime)  | ISO 8601 formatted date and time expressed with millisecond precision that represents when the [Entity](#entity) was created or added to a data set.  Analogous to [sdo:dateCreated](http://schema.org/dateCreated). | 0..1 |
| dateModified | [xsd:dateTime]( https://www.w3.org/TR/xmlschema11-2/#dateTime) | ISO 8601 formatted  date and time expressed with millisecond precision that represents when the [Entity](#entity) was last modified.  Analogous to [sdo:dateModified](http://schema.org/dateModified) | 0..1 |

__Requirements:__ an [Entity](#entity) *should* be provisioned with a globally-scoped, dereferenceable IRI in order to ensure that [Event](#event) data can be linked and shared.  In cases where an IRI is inappropriate, an [Entity](#entity) can be assigned a blank node identifier.

__Subclasses__

[Agent](#agent), [Attempt](#attempt), [AudioObject](#audioobject), [Collection](#collection), [DigitalResource](#digitalresource), [Forum](#forum), [ImageObject](#imageobject), [MediaObject](#mediaobject), [Membership](#membership), [Message](#message), [Organization](#organization), [Person](#person), [Thread](#thread), [Session](#session), [SoftwareApplication](#softwareapplication), [VideoObject](#videoobject)

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

__type:__ [http://purl.imsglobal.org/caliper/v1/Agent](http://purl.imsglobal.org/caliper/v1/Agent)

__Comment:__ a [clpr:Agent](#agent) is a generic class that represents a [clpr:Entity](#entity) that can initiate or perform an [Action]([#appendixA).  It is analogous to a [foaf:Agent](http://xmlns.com/foaf/spec/#term_Agent).  Given that [clpr:Agent](#agent) represents a generic type it is *recommended* that only subclasses of [clpr:Agent](#agent) be used to represent a [clpr:actor](#actor).

__Subclasses:__ [Person](#person), [Organization](#organization) and [SoftwareApplication](#softwareapplication)