---
title: Projects
icon: fa-envelope
order: 2
---
<style>
  .tech li{
    list-style: none;
    margin: 5px;
    border: 2px solid grey;
    border-radius: 20px;
    padding-left: 10px;
    padding-right: 10px;
  }
  .tech{
        display: flex;
  }
</style>


## Provide a regionally distributed API Gateway

<div style="display: flex;flex-direction: row;justify-content: space-between;">
<div style="font-size:1.2em;font-weight:600;">Solution Architect</div><div>January 2019 - now</div>
</div>

<div style="text-align: left;">
Due to the current service landscape of the customer, we found that most commercially available API gateways are not prepared to provide its functionality across multiple regions/continents within a consolidated environment. Therefore we initiated this project to provide a basic API gateway (as a layered architecture) to provide API functionality internally as well as expose a certain subset publicly. All this was created on top of an existing ESB architecture, which also provided basic building blocks for deployment and monitoring.
</div>
<br>
Used technologies:
<ul class="tech">
<li>API</li>
<li>API Gateway</li>
<li>WSO2 Ballerina</li>
<li>Consul</li>
<li>TIBCO ESB</li>
</ul>


## callable.cloud

<div style="    display: flex;
    flex-direction: row;
    justify-content: space-between;">
<div style="font-size:1.2em;font-weight:600;">Full Stack Developer</div><div>July 2018 - May 2019</div>
</div>

<div style="text-align: left;">
Callable is a SaaS project which aims to provide a serverless integration for SAP systems.<br>
It provides OpenAPI access to any SAP-based system through SAP-native mechanisms (SAP JCO). Through the transformation from SAP JCO types into restful interfaces, interacting with such systems is opened to a much broader audience. This system is completely built on serverless components to keep the offset cost at a bare minimum. The licensing also follows a pay-per-use model.
</div>
<br>
Used technologies:
<ul class="tech">
<li>API</li>
<li>Amazon Web Services</li>
<li>SAP</li>
<li>OpenAPI</li>
<li>SaaS</li>
</ul>


## Build B2B API for booking system

<div style="    display: flex;
    flex-direction: row;
    justify-content: space-between;">
<div style="font-size:1.2em;font-weight:600;">Solution Architect / Full Stack Developer</div><div>October 2017 - June 2018</div>
</div>

<div style="text-align: left;">
Exposing previously private interfaces to business partners, which allows them to request the necessary information to streamline the booking process. Those interfaces include schedule and routing information required for a decision making on the actual freight forwarder.<br>
The project decided to implement this in the form of a public API within the AWS ecosystem.<br>
AWS API Gateway was chosen to provide a secured endpoint.<br>
AWS Lambda was chosen to implement a transformation into internal formats and routing into the company DMZ.<br>
The On-premise stack consisted of a TIBCO ESB which we connected to AWS Lambda to transport the information to the backend.
</div>
<br>
Used technologies:
<ul class="tech">
<li>API</li>
<li>Amazon Web Services</li>
<li>API Gateway</li>
<li>AWS Lambda</li>
<li>TIBCO ESB</li>
<li>JMS</li>
</ul>

