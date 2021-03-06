---
slug: api-first-development
title: API First Development
---

One message we continually try to re-iterate is the importance of Services (aka APIs) having a well-defined coarse-grained Services Contract 
which serves as the interface into your system by which all external consumers bind to - making it the most important contract in your system.

A strategy we recommend for maximizing re-use of your Services is to design them from an API-first point of view where all consumers 
(e.g. Desktop, Mobile and Web UIs) have equal accessibility to your services since they all consume the same published API's for all of 
their functionality.

### Benefits of Services

This is the development model ServiceStack has always promoted and what most of its features are centered around, where your Services Contract is 
defined by decoupled impl-free DTOs. If your Services retain this property then they'll be able to encapsulate any of its capabilities of 
infinite complexity and make it available remotely to all consumers with never any more complexity than the cost of a Service call:

![](https://raw.githubusercontent.com/ServiceStack/docs/master/docs/images/dtos-role.png)

This is where the **true value** of Services are derived, they're the ultimate form of encapsulating complexity and offers the highest level 
of software reuse. ServiceStack amplifies your Services capabilities by making them available in multiple [Hosting Options](/why-servicestack#multiple-hosting-options), 
[serialization formats](/why-servicestack#multiple-pluggable-formats), [MQ and SOAP endpoints](/why-servicestack#multiple-endpoints) to
enable more seamless integrations in a variety of different scenarios including native end-to-end Typed APIs for the most popular 
[Web, Mobile and Desktop Apps](/why-servicestack#multiple-clients) that reduce the effort and complexity required to call your Services 
in all consumers - multiplicatively increasing the value provided.

### API First Development Model

The practice .NET has always dictated was that you need to maintain **separate controllers** and logic for your **HTML UIs** and a **different controller** 
for your **HTTP APIs**. Apart from forcing code duplication, doing this breaks your systems well-defined Service Contracts where any custom
logic in your MVC Controllers and Razor pages becomes another entry point into your system where no longer are all your system capabilities available 
to all clients, some are only available when using a browser to navigate MVC pages.

Whereas in ServiceStack there are only Services, which are written with pure logic that's unopinionated as to what clients are calling it, with 
clean **Request DTOs** received as Inputs that typically return clean **Response DTOs** as outputs. HTML is then just another serialization format, 
providing a View of your Services or serving as a bundled UI that works on top of your existing Services, in all cases calling the same 
well tested and defined Services that all other clients use.

For web development this means that UI logic and Error handling should ideally be utilizing the pure API Error Responses rather than behind 
server-side pages which gets easily coupled to your server implementation rather than your external published APIs. 

### Validation by all the things

To better demonstrate the benefits of this approach and and show how there's no loss of flexibility, we've created the 
[World Validation](https://github.com/NetCoreApps/Validation) .NET Core App which uses the same pure unopinionated ServiceStack Services to support 
**8 different HTML UI strategies** including server HTML Rendered and Ajax Client forms, multiple View Engines, multiple layouts - all utilizing 
the same Services and declarative [Fluent Validation](/validation).

[![](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/apps/Validation/home.png)](https://github.com/NetCoreApps/Validation)

<h4 align="center">View Source on GitHub <a href="https://github.com/NetCoreApps/Validation">NetCoreApps/Validation</a></h4>

It should be noted that these are just examples of different HTML UIs, with no additional effort, all ServiceStack Services automatically
provide native integrations into **all popular Mobile and Desktop Apps** with [Add ServiceStack Reference](/add-servicestack-reference). 

## [World Validation](/world-validation)

The annotated [World Validation Docs](/world-validation) walks through and showcases the implementation of how the most popular **Server HTML rendered**
approaches and **Client UI rendered** technologies which are able all to use the same single suite of ServiceStack Services.
