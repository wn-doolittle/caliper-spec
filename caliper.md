### Table of Contents
* [Namespaces](#namespaces)
*	[Appendix A: Caliper Actions](#appendixA) 

<a name="namespaces"/>  

### 1.x Namespaces

The Caliper information model references a number of terms derived from other ontologies.  Such terms along with those native to Caliper are identified with a prefix drawn from the list below that maps to the relevant namespace as, for example, the data type xsd:dateTime.

| Prefix | Namespace | Description |
| ------ | --------- | ----------- |
| clpr | http://purl.imsglobal.org/caliper/v1/ | Caliper |
| clpract | http://purl.imsglobal.org/vocab/caliper/v1/action# | Caliper action Vocabulary |
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


<a name="appendixA"/>  
 
### Appendix A: Caliper Actions

| Label | IRI | WordNet Gloss |
| ------ | --- | ------------- |
| created | http://purl.imsglobal.org/vocab/caliper/v1/action#Created | [create](http://wordnet-rdf.princeton.edu/wn31/201620211-v): make or cause to be or to become |
| deleted | http://purl.imsglobal.org/vocab/caliper/v1/action#Deleted | [delete](http://wordnet-rdf.princeton.edu/wn31/201001860-v): wipe out digitally |
| markedAsRead | http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead | [mark](http://wordnet-rdf.princeton.edu/wn31/200923709-v): designate as if by a mark, [read](http://wordnet-rdf.princeton.edu/wn31/200626756-v): interpret something that is written or printed |
| markedAsUnread | http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsUnread | inverse of markedAsRead |
| posted | http://purl.imsglobal.org/vocab/caliper/v1/action#Posted | [post](http://wordnet-rdf.princeton.edu/wn31/201033289-v): to cause to be directed or transmitted to another place |
| removed | http://purl.imsglobal.org/vocab/caliper/v1/action#Removed | [remove](http://wordnet-rdf.princeton.edu/wn31/200181704-v): remove from sight |
| subscribed | http://purl.imsglobal.org/vocab/caliper/v1/action#Subscribed | [subscribe](http://wordnet-rdf.princeton.edu/wn31/202214527-v): receive or obtain regularly |
| updated | http://purl.imsglobal.org/vocab/caliper/v1/action#MarkedAsRead | [update](http://wordnet-rdf.princeton.edu/wn31/200835207-v): bring up to date; supply with recent information |
| unsubscribed | http://purl.imsglobal.org/vocab/caliper/v1/action#Unsubscribed | inverse of subscribed |