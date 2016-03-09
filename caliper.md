### Table of Contents
* 1.x. [Namespaces](#namespaces)
* 1.x. [Definitions](#definitions)
* X.x. [Contributors](#contributors)
*	[Appendix A: Caliper Actions](#appendixA) 


<a name="definitions"/>  

### 1.x. Definitions

__blank node__: A locally-scoped identifier that is used to refer to a resource when a globally scoped identifier is either inappropriate, as in the case of transient data, or not provided.  A blank node is prefixed with an underscore (_) and is scoped to the document in which it is used (e.g., _:a1).

__JSON-LD__:  TODO

__IRI__: The Internationalized Resource Identifier (IRI) extends the Uniform Resource Identifier (URI) scheme by using characters drawn from the Universal Character Set rather than ASCII.  The IRI is a globally scoped identifier used in linked data to refer to most nodes and properties.  An IRI reference may be absolute or relative to that of another absolute IRI.  In JSON-LD relative IRIs are resolved relative to the base IRI.

__ISO 8601__: Caliper time values are formatted per ISO 8601 with the addition of millisecond precision.  The format is yyyy-MM-ddTHH:mm:ss.SSSZ where 'T' separates the date from the time while 'Z' indicates that the time is in UTC. 

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

<a name="contributors"/>

### X.x Contributors

The following Caliper Working Group participants contributed to the writing of this specification:

| Name | Organization |
| ------ | --------- |
| Anthony Whyte | University of Michigan |


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