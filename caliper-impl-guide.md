# IMS Caliper Analytics&reg; Implementation Guide, version 1.1

## IPR and Distribution Notices

Recipients of this document are requested to submit, with their comments, notification of any relevant patent claims or other intellectual property rights of which they may be aware that might be infringed by any implementation of the specification set forth in this document, and to provide supporting documentation.

IMS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on IMS’s procedures with respect to rights in IMS specifications can be found at the IMS Intellectual Property Rights web page: [http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf](http://www.imsglobal.org/ipr/imsipr_policyFinal.pdf).

Copyright &copy; 2018 IMS Global Learning Consortium. All Rights Reserved.

Use of this guide to develop products or services is governed by the license with IMS found on the IMS website: http://www.imsglobal.org/speclicense.html.

Permission is granted to all parties to use excerpts from this document as needed in producing requests for proposals.

The limited permissions granted above are perpetual and will not be revoked by IMS or its successors or assigns.

THIS GUIDE IS BEING OFFERED WITHOUT ANY WARRANTY WHATSOEVER, AND IN PARTICULAR, ANY WARRANTY OF NON INFRINGEMENT IS EXPRESSLY DISCLAIMED. ANY USE OF THIS GUIDE SHALL BE MADE ENTIRELY AT THE IMPLEMENTER'S OWN RISK, AND NEITHER THE CONSORTIUM, NOR ANY OF ITS MEMBERS OR SUBMITTERS, SHALL HAVE ANY LIABILITY WHATSOEVER TO ANY IMPLEMENTER OR THIRD PARTY FOR ANY DAMAGES OF ANY NATURE WHATSOEVER, DIRECTLY OR INDIRECTLY, ARISING FROM THE USE OF THIS GUIDE.

## Table of Contents
* 1.0 [Introduction](#introduction)
  * 1.1 [Status of this Document](#docStatus)
  * 1.2 [Terminology](#terminology)
  * 1.3 [Metric Profiles](#profiles)
  * 1.4 [Engagement Scenario](#engagementScenario)
* 2.0 [Quick Start Guide](#quickStartGuide)
  * 2.1 [Download the reference Caliper Sensor implementation](#download)
  * 2.2 [Build sensor project, run unit tests and deploy](#build)
  * 2.3 [Install the sensor in your application](#install)
* 2.4 [View your events using an HTTP Request Inspector](#view)
* 2.5 [Store your events using a Caliper Reference Event Store Implementation](#store)
* 2.6 [Process for Implementing a Caliper Event Store](#process)
* 2.7 [Implement and send an event in your application](#implement)
* 2.8 [LTI&reg; Connectivity (If you are an LTI&reg; compliant Provider/tool)](#lti)
* 3.0 [Best Practice Guidelines](#bestPractices)
  * 3.1 [How best to manage event size to send across the wire?](#eventSize)
    * 3.1.1 [Use the Sensor API DESCRIBE method with an object to qualify events with more educational context](#useDescribe)
    * 3.1.2 [Use the JSON-LD `@id`, `@type` and `@context` to request the data](#useJsonld)
    * 3.1.3 [Send all the events complete with detailed information](#sendCompleteEvents)
  * 3.2 [LTI Best Practices](#ltiBestPractices)
  * 3.3 [Authentication suggestions](#authBestPractices)
  * 3.4 [SSL/HTTPS](#httpBestPractices)
  * 3.5 [How do I transmit additional information that is not included in the Metric Profiles?](#extensionsBestPractices)
    * 3.5.1 [You can add additional key/value pairs to an Entity’s extensions property](#extensionsKeyValuePairs)
  * 3.6 [Envelope for the Metric Profile](#envelope)
* [About This Document](#aboutDoc)
* [List of Contributors](#contributors)
* [Revision History](#revisionHistory)

## <a name="introduction"></a>1.0 Introduction
As part of developing the Caliper Analytics&reg; standard and sensor reference architecture, the development team and implementers of the proof of concepts have come up with a best practice guide, including a quick start section.

The purpose of this document is to provide you with a detailed exploration of how Caliper works and the issues that arise so as to give you guidance on good practice, if not, best practice.

Please provide feedback based on your own experiences to help improve the quality of the recommendations included here.

### <a name="docStatus"></a>1.1 Status of this Document
This document is considered the _Final Release_.  This means that the Caliper Analytics&reg; Implementation Guide, version 1.1, is now made available as a public document following acceptance by IMS Global member organizations, a number of whom have successfully achieved conformance certification at the time of the release of this document.
    
IMS Global strongly encourages its members and the greater public to provide feedback that focuses on improving the Caliper specification. To join the IMS developer and conformance certification community focused on Caliper please visit https://www.imsglobal.org/activity/caliper.
    
Public comments and questions can be posted at the Caliper Analytics&reg; [public forum](https://www.imsglobal.org/forums/ims-glc-public-forums-and-resources/caliper-analytics-public-forum).

### <a name="terminology"></a>1.2  Terminology
We will start with a bit of terminology to help make the descriptions that follow more precise.  The Caliper specification uses the following terms:

<a name="caliperDef"></a>__Caliper__: the name of the IMS Caliper Analytics&reg; Learning Measurement Framework which provides a standard for representing, capturing, and marshalling metrics generated by learning activity and targeted for consumption by any conforming analytics store or service.

<a name="learningActivityDef"></a>__Learning Activity__: Any activity considered a component of a learning sequence presented in a digital learning environment (e.g. LTI&reg; tool) typically denoted as a lesson.  Activities can be assignable and/or gradable as required.

<a name="sensorApiDef"></a>__Caliper Sensor API&trade;__: defines and specifies interaction between Learning Application and Caliper.

<a name="sensorDef"></a>__Caliper Sensor__:  code/library that assists in the measurement of Caliper Events.  Deployed into the Learning/Digital Application.  Sensors are implemented in Java, Javascript, PHP, Python, Ruby and .NET.

<a name="metricProfileDef"></a>__Metric Profile__: the Information Model for Caliper – organized by Learning Activity Type.

<a name="eventStoreDef"></a>__Event Store__: System or software service that stores event data emitted by the Caliper Sensors.
 
### <a name="profiles"></a>1.3 Metric Profiles
The Metric Profiles represent the Information Model and are organized by Learning Activity type.  When you begin implementing Caliper you should compare your application’s features with the metric profiles and implement the ones necessary to capture the user’s activities based on your features.  For example a Quizzing tool would want to implement base, session, assessment, assessment item and outcome metric profiles. An eReader would at a minimum implement base, session and reading metric profiles.

A complete list of the metric profiles and detailed information about each including properties and their data types, description, source and whether they are required are included in the [Implementation Guide](https://www.imsglobal.org/caliper/caliperv1p0/ims-caliper-analytics-implementation-guide).

| Profile | What can I use it for? |
| :------- | :----------- |
| Base | Represents the base Caliper `Event`, `Entity`, and actions used in other profiles |
| Session | Track users as they log in, log out, and also session time outs across multiple eduApps |
| Reading | Track engagement of users with reading material – navigation to/from, pages, etc.  Leverages ePUB, IMS Learning Information Services (LIS) and schema.org vocabularies |
| Annotation | Track learning activity related to bookmarks, highlights, sharing, notes, attachments, tagging and recommendations.   Leverages schema.org, LIS and OpenAnnotations vocabularies |
| Media | Track learning activity related to multi-media objects – Video, Audio and Image media types.  Leverages schema.org and LIS vocabularies |
| Assignable | Track learning activity on Assignable objects.  This profile allows you to make any object (e.g. reading, media, assessments, etc.) “assignable”.  Leverages schema.org and LIS vocabularies |
| Assessment | Track learning activity on Assessments.  Leverages LIS, Question and Test Interoperability&reg; (QTI&reg;), schema.org vocabularies |
| Outcomes | Track outcomes (Results) on assignable objects.  Leverages LIS Outcomes vocabulary |
| Engagement Scenario | Not a metric profile per se, but one common scenario / applied use case that applies a blended collection of metrics and context derived from other metric profile elements to explicitly collect engagement activity/usage associated data across a wide spectrum of learning activities |

### <a name="engagementScenario"></a>1.4  Engagement Scenario
This scenario contains a list of Events and corresponding actions from the current set of Caliper Metric Profiles that indicate minimum student engagement with Learning Activities.

In order to quantify engagement, three elements can be measured:

* the overall duration of a “session” comprising multiple events;
* the duration of engagement with each individual activity; and, 
* the total number of (each) type of `Event` in a session.

Each `Event` has an “opening” action that indicates engagement, e.g. “started”.  Other actions in the sequence (e.g. paused, resumed, completed) can also be included, including a “closing” action to indicate the end of a sequence.  However, to simply get an indicator of (one or many) students engagement with a specific Learning Activity, the opening action could be sufficient.

All attributes/objects (e.g. `actor`, `action`, `object`, `startedAtTime`, `endedAtTime`, `duration`, etc) of Events are implicitly part of the Engagement Profile.

| Event | Action | Metric Profile | Comments |
| :---- | :----- | :------------- | :------- |
| `SessionEvent` | loggedIn | Session | &nbsp; |
| `NavigationEvent` | navigatedTo | Multiple | Common across all Learning Activity types |
| `ViewedEvent` | viewed | Reading | &nbsp; |
| `AnnotationEvent` | All | Annotation | &nbsp; |
| `MediaEvent` | started, paused, resumed, etc. | Media | &nbsp; |
| `AssignableEvent` | started, completed, submitted | Assignable | &nbsp; |
| `AssessementEvent` | started, submitted | Assessment | &nbsp; |

## <a name="quickStartGuide"></a>2.0  Quick Start Guide
In order to make it easier for programmers to get started implementing Caliper, we have created a [Getting Started Video](http://youtu.be/0AHKZpaPD2k).

There is also an exercise in Plunker written in Javascript that will walk a developer through implementing a caliper sensor.  The application is modeled as a simple Course delivery app, that delivers a syllabus, reading and quiz. Here is the link to the [Sample Application](http://plnkr.co/edit/6uRssC6aGXdXWK4l1UjX?p=info).

### <a name="download"></a>2.1  Download the reference Caliper Sensor implementation.
The first step in implementing the Caliper sensor is to download the reference Caliper Sensor implementation that is applicable to your technology stack.  The links below point to the Github repository for each sensor.

* Java - [Caliper Java Sensor](https://github.com/IMSGlobal/caliper-java-public)
* Javascript - [Caliper Javascript Sensor](https://github.com/IMSGlobal/caliper-js-public)
* PHP - [Caliper PHP Sensor](https://github.com/IMSGlobal/caliper-php-public)
* .NET - [Caliper .NET Sensor](https://github.com/IMSGlobal/caliper-net-public)
* Python - [Caliper Python Sensor](https://github.com/IMSGlobal/caliper-python-public)
* Ruby - [Caliper Ruby Sensor](https://github.com/IMSGlobal/caliper-ruby-public)

### <a name="build"></a>2.2  Build sensor project, run unit tests and deploy
Build the project and run the test suites using the directions in the project’s README. Based on the type of sensor, you can use it on the server (all sensor types) or the client (e.g. Javascript sensor, note also for client-side sensors please note the authentication-related suggestions to maximize security.)   The mechanism for using the sensor within your code will also vary depending upon the sensor.  For example, you would include the Java sensor as a Maven dependency, the Ruby sensor as a Ruby Gem, the Python sensor as a Python Module, etc.  Each individual README provides information on this.

* Java – Web App (Server)
* Javascript – Node.js (Server), Mobile (Browser), Web (Browser)
* PHP – PHP Web App (Server)
* .NET – Windows (Server)
* Python – Django, Bottle (Server)
* Ruby – RoR, Sinatra (Server)

### <a name="install"></a>2.3  Install the sensor in your application
Install the sensor into your application following the instructions in the README. 

e.g., for Javascript: 

Install the caliper sensor into your application by placing the URL of the Caliper sensor Javascript library. 

```
<script src="http://www.imsglobal.org/caliper/caliperSensor-1.0.0.js"></script>
```

### <a name="view"></a>2.4  View your events using an HTTP Request Inspector
You will need a place to capture events emitted by the Caliper Sensor.  The sensor sends events as a HTTP POST to a RESTful service.

For a very quick start, you can use a tool that allows you to inspect HTTP requests such as [RequestBin](http://requestb.in/).  This will allow you access to the events being sent so you can inspect them and decouple the Event Store implementation from testing the sensor and `Event` generation.

In addition, you can also send events to the Caliper Conformance Service located here: [Conformance Test Suite](http://caliper.imsglobal.org/)

### <a name="store"></a>2.5  Store your events using a Caliper Reference Event Store Implementation
The Caliper team has provided a reference EventStore implementation.  The EventStore is intended as a development/test/demo environment and is not intended for use as part of a production implementation of Caliper.  You can find it at: [Event Store](https://github.com/IMSGlobal/caliper-eventstore-public).    

Follow the directions in the readme, to get the reference implementation of the Event Store up and running.

Each sensor needs to be updated to include the correct endpoint for the datastore that you have up and running.

### <a name="process"></a>2.6  Process for Implementing a Caliper Event Store
Additional best practices, implementation guidelines and possible alternative supporting event stores are currently underway and forthcoming as both Caliper, event store technologies and related support matures.  For now, utilizing the current Caliper Reference Event Store as a guide and understanding the JSON-LD based event stream so as to adapt any potential target persistence or event consuming service is a good starting point.   Further information and assistance will be provided by the IMS Caliper work group upon request. 

### <a name="implement"></a>2.7  Implement and send an event in your application
Select sensor code bindings may include a sample application that provides implementation details for your chosen technology.  Currently, sample applications have been written in Java, Javascript and .NET.   Sample applications for the other sensors will be developed as time and interest permits.

Available Sample Applications

 [Java Sample Application](https://github.com/IMSGlobal/caliper-java-example-public)

Let’s take a look at the pieces that make up a Caliper `Event`, using a `NavigationEvent` as the stepwise example:

1. Set the actor to be the current user (i.e. that was passed over in the LTI launch, or equivalent as part of the application context).
2. Set the action for the `Event`, in this case Caliper.Actions.ReadingActions.NAVIGATED_TO.
3. Set the Object being interacted with by the Actor.
4. Set the Target Object within the `Event` Object.
5. Set the Educational Application (`edApp`) that is part of this Learning Context.
6. Set the organization, which is the LIS course section that is part of this learning action.
7. Set the navigatedFrom Object, which is the location from where the user navigated from.  This gives you the ability to create a graph of user actions.
8. Set the eventTime for the navigation. 
9. Add any other optional information that you want to include in the `Event` message.
10. Send the `NavigationEvent` using the sensor.

### <a name="lti"></a>2.8  LTI&reg; Connectivity (If you are an LTI compliant Provider /tool)
For full detail please refer to the IMS Global Learning Tools Interoperability&reg; Caliper - LTI - Implementation Guide.

| Item | Description | Value Type |
| :--- | :---------- | :--------- | 
| Event Store URL | Endpoint for Caliper service messages | URL |
| Caliper API key | Key to identify system owner of message data | Variable length string. Minimally a 128 bit UUID (e.g. RFC 4122 like UUID), but other (and possibly more secure) keys are preferable |
| Caliper Profile URL | The endpoint for the Caliper Profile Service | URL |
| Federated Session Identifier | A URI that represents a federated LTI+Caliper set of launches/interactions (changes per session) | URI |
| Caliper Sensor Id | A key that represents a Caliper Sensor installed within a system (Tool Consumer or Provider) | Opaque String (Ideally a URI) |

## <a name="bestPractices"></a>3.0  Best Practice Guidelines

### <a name="eventSize"></a>3.1  How best to manage event size to send across the wire?
The Caliper payload is sent inside an `Envelope`, that allows for multiple events to be grouped together

{
  "sensor": "https://learning-app.some-university.edu/sensor",
  "sendTime": "2015-09-15T11:05:01.000Z",
  "data": [ \<event1\>, \<event2\>, . . ., \<eventN\>]
}

The size of the event "data" list is up to the Tool Consumer/Provider to negotiate.

#### <a name="useDescribe"></a>3.1.1  Use the Sensor API&trade; DESCRIBE method with an object to qualify events with more educational context
The sensor includes a describe method  that can take either a Caliper `Entity` or array of Caliper Entities.  So you can set elements of the learning graph  that are consistent throughout a learner session and stream of events without having to specify such contextual elements each time an `Event` is sent  (i.e., the `edApp`, `group`, `session` etc.).  This provides a mechanism for reducing the size of serialized `Event` payloads .                                    

#### <a name="useJsonld"></a>3.1.2  Use the JSON-LD `@id`, `@type` and `@context` to request the data.
Since all Caliper Entities include a JSON-LD `@id`, `@type` and `@context`, you can specify larger and possibly more secondary event data entities independent from the `Event` itself and therefore only the @id transmitted which can optionally be dereferenced as required  to retrieve all of the additional information provided by a given event related service.

#### <a name="sendCompleteEvents"></a>3.1.3  Send all the events complete with detailed information.
 Another option is to send detailed information for all the event-related entities.  That said, be sure to specify null values for anything unspecified that is to sent across the wire.  There is optimizing compression etc during the serialization process to mitigate somewhat the event payload size.  In future revisions of Caliper there are plans to continue to streamline the event payloads via optimizations in the event model itself.

### <a name="ltiBestPractices"></a>3.2  LTI Best Practices
In order to preserve the confidentiality of the shared secret, this data item is not passed in an LTI launch request.  Instead a Caliper Profile service should be declared in the tool consumer profile which may then be used by the tool provider to obtain the secret via a server-to-server web service request.

For full detail please refer to the IMS Global Learning Tools Interoperability&reg; Caliper - LTI - Implementation Guide.

### <a name="authBestPractices"></a>3.3  Authentication suggestions
For Caliper launches from an LTI Consumer/Provider the LTI security context is passed on. 

Without LTI integration, the Caliper Sensor API&trade; endpoint is secured via similar LTI-OAuth signing and key/secret exchange .  As a best practice we recommend the use of OAuth. 

The calls to an Event Store should be secured by an API Key.  For the Javascript sensors the call to the Consumer Event Store should be performed server-to-server to ensure the integrity of the key.  The API key is stored  in the authorization header.

### <a name="httpBestPractices"></a>3.4  SSL/HTTPS
Caliper strongly recommends SSL/HTTPS for everything going over the wire.  Caliper Event Store endpoints should be secured by SSL to ensure secure communications.  The Sensors should accept and transmit through SSL/HTTPS.

### <a name="extensionsBestPractices"></a>3.5 How do I transmit additional information that is not included in the Metric Profiles?
You have two options if you require additional information to be sent over the wire that are not included by default in the metric profile.                         

#### <a name="extensionsKeyValuePairs"></a>3.5.1  You can add additional key/value pairs  to an Entity’s extensions property.
The extensions property is a dictionary that can contain a list of properties.  So for example you can add: 

```
"extensions": {
  "com.vendor.example.myNeededProperty": "its value"
}
```

Extensions should use a technique to ensure uniqueness across organizations (for example, a reverse-domain formatted string).  Extend the Caliper JSON-LD `Event` schema 

Another option would be to extend the appropriate Caliper Metric Profile JSON-LD `Event` schema with additional properties.

### <a name="envelope"></a>3.6  Envelope for the Metric Profile
The method envelope standard for all Caliper `Event` sequences includes:

```
{
  "sensor": "http://learning-app.some-university.edu/sensor",
  "sendTime": "2015-09-15T11:05:01.000Z",
  "data": [ {event1}, {event2}, …, {eventN}]
}
```

## Purdue’s use of Caliper
### Storage Platform
#### Data store design choices
Because Caliper data is transmitted as JSON, our initial implementation of the physical store, based on our intuition, used a document database similar to MongoDB (Microsoft Azure’s DocumentDB). As we dug deeper into the design of our data store, we found that a document database would make analysis and reporting difficult due to the highly relational nature of Caliper data. Thus, we initiated a proof of concept using a graph database for the physical store. We investigated several graph databases and chose Neo4j due to its open source license as well as its feature set and ability to scale. We were pleased with the results of the proof of concept, finding that Neo4j’s Cypher query language allowed us to have a great deal of flexibility in analyzing and visualizing Caliper data. Its enterprise-level capabilities and its maturity were also strong considerations. Because Caliper data is highly time-correlated, we leveraged the advantages of a graph database to use the “GraphAware Neo4j TimeTree” to make time-based queries more efficient.

While the advantages to using a graph database are many for highly relational data like Caliper, a design trade-off we had to consider was the fact that a graph database has much higher memory requirements to be performant. In addition, the technology is newer and may have some rough edges. Additionally, inserts into Neo4j (and probably other graph databases) are relatively slow vs. a document database. Finally, we found cloud-based Neo4j providers to be uncommon and fairly expensive, so we elected to host our own. Thus the tradeoff of having to sysadmin a VM running Neo4j.

In order to mitigate the costs of some of these tradeoffs, we intend to move to a more traditional OLTP/ODS model in the future where the Caliper requests are stored as documents in a document database. There will be a separate, asynchronous process that deserializes the documents from the document database into the graph database which will be used for analysis and reporting.

#### Collection endpoint
Because we are using a graph database, every request to our event store results in the Caliper payload being deserialized into an object graph that gets persisted to the Neo4j database. Because the distinction between entities and events is a semantic distinction, we found no technical reason to host both /entities and /events endpoints. We ended up choosing to implement a /collector endpoint that receives both entities and events, delegating validation and deserialization to the appropriate services.

###  Authorization
#### Authorizing tools
Our Caliper datastore uses OAuth bearer tokens, as specified in the Caliper documentation, to restrict access to the /collector endpoint.

In the process of designing our datastore, we asserted that identity management was a feature better served by tool providers than by the Caliper data store itself. As such, we chose to delegate identity management and bearer token issuance to each of the tool providers. The Caliper data store maintains a set of trusted tool providers that are authorized to act as a proxy for the issuance of OAuth bearer tokens. The trusted clients authenticate via the OAuth client credentials flow. In order to obtain a bearer token that can be used by the Caliper sensor within each of the tool providers, the user must authenticate to the tool provider first. After that, the sensor can request an OAuth token for use with the Caliper data store from the tool provider.

### Validation
From the initial conception of our Caliper Event Store we wanted to treat it as an authoritative source for reporting and analysis to drive technology decisions. In order to trust the data in the Event Store, we came to the conclusion that we must validate the data as it streams in. This provided a non-trivial challenge, since the Caliper 1.0 spec contains a multitude of Events, Entities, and relations between them. Taking into consideration the nature of the JSON-LD payloads, we wrote a JSON Schema from scratch that could be used to easily validate the incoming Caliper Events and Entities. This allowed us to persist the data with confidence, and ensure our tool sensors were correctly implemented.

### Lifecycle Management
The initial use case for our Caliper sensor and endpoint/data store implementations was the storage of session data in order to determine usage of our tools. To this end, we conform to the Caliper Session Profile by tracking session starts and ends. We knew from the beginning that once we added the Caliper sensor into one of our tools, the other tools would follow shortly after. In the process of implementing Caliper in our first tool, we learned there would be a large amount of logic that could be shared from tool to tool. For this reason we created common library services for JavaScript, iOS, and Android, in order to encapsulate the common lifecycle logic shared across applications. Creating these shared libraries allowed us to implement cross-cutting features such as a persistent queue, session keep-alive, and session timeout logic.

#### Persistent Queue
As users interact with our tools, we want to ensure that we minimize the possibility of lost data. For web-based tools, Events and Entities are saved to a queue that is persisted to localStorage on web and to disk on mobile. This queue is periodically sent to the Event Store. Implementing this queue allowed for reduced load on the Event Store APIs, as well as persisting data across browser sessions and reducing the risk of intermittent network errors. In the case of a failed HTTP request to the Event Store, the data remains in the queue to be retried later.

#### Sessions on web
One issue we encountered when adding Caliper to our web-based tools was how to handle the session lifecycle. We wanted to more accurately capture when a user was actually active in each tool versus when their tokens were refreshed, or when they navigated between pages. Additional complexity was encountered when updating our legacy .NET MVC applications. We still wanted to re-use our JavaScript based library for managing the Caliper tracking and persisting sessions across page refreshes. The solution we developed was to leverage the browser’s localStorage to track a “last active date”, automatically updating this based on user interactions. As long as the user continues to interact with the site their session remains active. We send a periodic “keep-alive” to the Event Store, updating the Session entity’s dateModified property. Once a user is idle for a period of time, their session is ended at the last known active date once they return to the tool. Adding the session keep-alive and timeout features  allowed us to use our library to instrument all of our apps built in .NET MVC, Angular, or React.

#### Sessions on mobile
While web sessions were complex to track, sessions on mobile are more straightforward. We consider a session started when the app comes to the foreground and ended when it moves to the background.

### Mobile
We’ve added Caliper to three different platforms: native iOS, native Android, and React Native. After implementing Caliper, when looking at our tool usage we found that for several of our apps, more than 70% of our users have used the corresponding mobile app. The percentage of sessions coming from our mobile apps is even higher than the percentage of users. It’s worth noting that the reason for the high percentage of sessions coming from mobile isn’t solely usage. Mobile sessions tend to be shorter. For one of our mobile apps, 75% of sessions are less than a minute long. Moving forward we may consider measures to add minimum session limits.

### Reporting
The driving force behind adding Caliper 1.0 to our learning tools was to be able to use the data for reporting and analysis. To this end we designed and created Scope, a dashboard built in React. We added reporting endpoints to our EventStore API that the dashboard can access to pull data about apps, users, and sessions over time.

## <a name="contributors"></a>List of Contributors
The following individuals contributed to the development of this document:

| Contributor | Affiliation |
| :---------- | :---------- |
| Anthony Whyte | University of Michigan |
| Viktor Haag | D2L |
| Gavin Brown | Purdue University |
| Jason Dufair | Purdue University |
| Will Grauvogel | Purdue University |
 
<a name="aboutThisDoc"></a>About this Document
IMS Global Learning Consortium, Inc. ("IMS Global") is publishing the information contained in this document ("Guide") for purposes of scientific, experimental, and scholarly collaboration only.

IMS Global makes no warranty or representation regarding the accuracy or completeness of the Guide.

This material is provided on an "As Is" and "As Available" basis.

The Guide is at all times subject to change and revision without notice.

It is your sole responsibility to evaluate the usefulness, accuracy, and completeness of the Guide as it relates to you.

IMS Global would appreciate receiving your comments and suggestions.

Please contact IMS Global through our website at [http://www.imsglobal.org](http://www.imsglobal.org).

Please refer to Document Name: IMS Caliper Analytics&reg; Implementation Guide, version 1.1

Date: XX MONTH 2018

This document contains trademarks of the IMS Global Learning Consortium including the IMS Logos, Learning Tools Interoperability&reg; (LTI&reg;), Accessible Portable Item Protocol&reg; (APIP&reg;), Question and Test Interoperability&reg; (QTI&reg;), Common Cartridge&reg; (CC&reg;), AccessForAll&trade;, OneRoster&reg;, Caliper Analytics&reg; and SensorAPI&trade;. For more information on the IMS trademark usage policy see trademark policy page - https://www.imsglobal.org/trademarks
