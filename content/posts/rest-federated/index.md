---
title: "Rest Federated"
slug: "Rest Federated"
description: "How to create a REST federated service"
date: 2023-08-27T14:17:30+02:00
draft: true
editURL: https://github.com/ace-astro/astronautsystems/issues
tags: ["REST", "API", "federation"]
showDateUpdated: true
---

**Federated REST API Service**

## Context

When the subject is "interfacing frontend applications with backend" it is possible to identify two alternatives: REST and GraphQL.
If there is a desire to implement a federated service there is no solution other than going GraphQL.
It is true that GraphQL brings, among many advantages, the possibility to have a federation between front and back, but they are independent concepts.

I will be using the terms front(end) and back(end) to describe: a consumer of an API and one or more API providers (that are not federated), respectivelly.

### Federation

> An encompassing political or societal entity formed by uniting smaller or more localized entities: such as a federal government or an union (Merriam-Webster)

> In a nutshell, API Federation is the set of design principles, tools, and infrastructure that make it possible to expose a set of services and event streams within a particular bounded context as a unified and consistent API for external customers, while allowing individual services within the bounded context to evolve and change without additional restrictions. ([Salesforce, Antonio Garrote 2023](https://engineering.salesforce.com/api-federation-growing-scalable-api-landscapes-a0f1f0dad506/))

In programming a federation could be any kind of group behind a comon interface.

So, the definition of _Federation REST API_ that I will be using is:

> A Backend service capable of grouping multiple APIs into a single contract in a way that is transparent to the caller.

### Implementation

Federation is so popular in GraphQL, that some documents fail to make a distinction.
I wish to implement this federation as a REST service.
This federation would connect with both front and back and it would require:

- That the backend(s) can provide an API contract in the form of OAS or RAML
- That the added federation dynamically implements endpoints given this contract
- That the addition of the fereration do not require any extra work from the client

Some of the questions I wish to address:

- How difficult would be to manage an extra layer between front and backend?
- How this management cost compares to the benefits that it brings?
- How performance could be affected by this extra layer
- What are the added benefits of adding this extra layer (observability, caching, authentification, authorisation, etc.)

## Architecture
 
Overall architecture diagram

![federated REST API service]()

### Features

- [ ] Dynamically manage endpoints based on a OAS definition
- [ ] Frontend code should be able to make the same API calls regardless of changes on the OAS difinition
- [ ] Given nultiple OAS documents this service should be able to merge them and make available a new OAS document that can be used by a client

## References
