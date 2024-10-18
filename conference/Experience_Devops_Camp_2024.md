# 1. Experiences from the DevOps Camp 2024

This readme is intended to collect my experiences from the [DevOps Camp](https://devops-camp.de/).

This article reflects the personal experiences and impressions of the author during the conference. The presentation does not reflect the official position or opinion of the organizers of the DevOps Camp.

- [1. Experiences from the DevOps Camp 2024](#1-experiences-from-the-devops-camp-2024)
- [2. General Procedure of the DevOps Camp](#2-general-procedure-of-the-devops-camp)
- [3. Day 1](#3-day-1)
  - [3.1. Keycloak](#31-keycloak)
  - [3.2. AWS Cost Commitments](#32-aws-cost-commitments)
  - [3.3. K8s Ingress vs. Gateway-API](#33-k8s-ingress-vs-gateway-api)
  - [3.4. Efficient DevSecOps Workflows with AI](#34-efficient-devsecops-workflows-with-ai)
  - [3.5. Devenv - Practical Introduction](#35-devenv---practical-introduction)
- [4. Day 2](#4-day-2)
  - [4.1. Open Construct Foundation - Why and How?](#41-open-construct-foundation---why-and-how)
  - [4.2. DevOps Culture Transformation](#42-devops-culture-transformation)
  - [4.3. Ansible Semaphore](#43-ansible-semaphore)
  - [4.4. Rapid Prototyping \& API-First in Action](#44-rapid-prototyping--api-first-in-action)


# 2. General Procedure of the DevOps Camp

The DevOps Camp is an__unconference__ where people from the fields of DevOps, administration and other IT-related areas meet.
At this event, a pool of topics is presented on each conference day. The agenda of topics will be presented at the start of each conference day.

The topics are presented in sessions of a maximum of 45 minutes. Any form is allowed, such as giving a presentation, demonstrating a live demo, starting a discussion round or the like.

# 3. Day 1

## 3.1. Keycloak

Brief introduction and presentation of the current release notes of [Keycloak](https://github.com/keycloak/keycloak).

Keycloak adds authentication to applications and secures services using user federation, strong authentication, user management, fine-grained authorization and more.

Despite using the tests under [running tests](https://github.com/keycloak/keycloak/blob/main/docs/tests.md) and [writing tests](https://github.com/keycloak/keycloak/blob/main/docs/tests-development.md), also [Testcontainers](https://github.com/testcontainers/testcontainers-java) based on Java can be used.

Further information have been found after the DevOps Camp under [Spring Boot – Keycloak Integration Testing with Testcontainers](https://www.baeldung.com/spring-boot-keycloak-integration-testing).

In addition, health checks can be queried via API endpoints [Enabling Keycloak Health checks](https://www.keycloak.org/server/health) and [metrics](https://www.keycloak.org/server/configuration-metrics).

With version [26.0.0](https://www.keycloak.org/docs/latest/release_notes/#keycloak-26-0-0) the following features are interesting:

- [Enabling Tracing](https://www.keycloak.org/server/tracing) with `OpenTelemetry`: detailed monitoring of each request's lifecycle
- `Organizations supported`: feature is now fully supported. Further documentation under [Enabling organizations in Keycloak](https://www.keycloak.org/docs/26.0.0/server_admin/#_enabling_organization_)

## 3.2. AWS Cost Commitments

During the presentation, there was an introduction to the [Saving Plans](https://docs.aws.amazon.com/savingsplans/latest/userguide/what-is-savings-plans.html) of AWS.
The Saving Plans provide various commitments to keep the costs for AWS products and services low.

A tool for determining the costs is the [AWS Pricing Calculator](https://calculator.aws/#/).
In addition to the tool, a tip was to cover the baseline of AWS resources through Saving Plans, because the discount for the commitment reduces the costs.
The peaks in resource performance can then be covered by On-Demand consumption.

## 3.3. K8s Ingress vs. Gateway-API

The documentation of the live demo is available at [DEVOPS-Camp 2024 -- kubernetes ingress vs. gateway-api](https://github.com/venc0r/devopscamp2024).

## 3.4. Efficient DevSecOps Workflows with AI

Presentation of possibilities for software generation via AI using the example of the AI assistant [GitLab Duo](https://about.gitlab.com/de-de/gitlab-duo/).

The documentation can be found under [Talk - Efficient DevSecOps Workflows With A Little Help From AI](https://gitlab.com/gitlab-da/use-cases/ai/ai-research/talk-efficient-devsecops-workflows-with-a-little-help-from-ai).

During the presentation, an example was shown where code in the Perl programming language was converted to Python.
The AI provided an output in Python that also corresponded to the functionality of the Perl program upon closer inspection.

From the audience came the experience that the code still needs to be covered by test suites, as it cannot be guaranteed that the functionality is really the same.

## 3.5. Devenv - Practical Introduction

[Devenv](https://devenv.sh/) is a development environment based on the package manager and programming language [Nix](https://nix.dev/manual/nix/2.18/language/index.html).

What was the use case for the usage of Devenv?

During PHP development in a Docker environment, the execution time on a MacBook was very long with several seconds.
The main reason for the increase was the virtualization overhead of Docker on the MAC.

What was the solution to the problem?

Use of Nix to run the PHP implementation without a virtual machine or container on the host's operating system.
Nix provides a "sandbox" approach to safely build and install packages.

Advantages of Devenv:

- Packages are built on the respective operating system (Linux, Windows, OS-X, ...) via Nix
- more control over the software environment
- better portability, security and scalability
- You can create Docker images from a Nix package, which become very compact through optimization
- Nix provides pre-built [packages](https://search.nixos.org/packages) for a variety of frameworks from their official package repositories
- In Nix, the version of the used framework can be specified directly.

# 4. Day 2

## 4.1. Open Construct Foundation - Why and How?

The session provides input on how the [Open Construct Foundation](https://www.openconstructfoundation.org/) was set up.
The Foundation is a non-profit organization that supports the community by building an ecosystem around the AWS CDK.

How did the start of the Foundation go?

1. Creation of a [Press Release & FAQ](https://www.open-constructs.org/#community-driven-cdk-construct-library)
2. Obtaining feedback on the press release from the stakeholders
3. Creation of a MVP that is then published with Press Release & FAQ
4. Cyclical releases with maintenance of an internal Press Release & FAQ for developers and stakeholders to keep the scope of functionality in mind

Important points:

- Open Source Contribution by the AWS Community, who submit improvements via Issues
  - Companies must also use these community-driven constructs
  - Maintenance via the AWS community who are passionate about driving its success
- The contributions are submitted via Merge Requests, which are publicly reviewed by the community

## 4.2. DevOps Culture Transformation

In this session, it was discussed what DevOps means for the audience and how it should be used in companies.

Output of the discussion:
- DevOps (Development and Operations) is a culture that, in simple terms, aims to develop and make software available to customers quickly and easily
- The usage should break down the separation of development and operations teams of an application
- DevOps is not really hung on a single engineer or a single team
- Separating platform, DevOps and development teams is a problematic development
- Architects play an important role in promoting collaboration between development and operations and supporting the technical implementation

## 4.3. Ansible Semaphore

Live demo of [Semaphore UI](https://github.com/semaphoreui/semaphore).

## 4.4. Rapid Prototyping & API-First in Action

Presentation of a use case for [Rapid Prototyping](https://sourcefranke.github.io/prototyping-apifirst-session/1).

Implementation of an [API demo](https://sourcefranke.github.io/clock-service-demo-api/) via a [YAML file and an NPM package](https://github.com/sourcefranke/clock-service-demo-impl).

Output of the discussion:
- Prototypes should normally not be directly incorporated into the implementation or production of a product
   -  Prototypes are simplified and incomplete, sometimes even with quality defects
   -  regulatory requirements and security standards are not met
- Assumptions made in prototypes should be clarified
- Define the target group of the prototype
   - For internal presentation, e.g. to product managers, it should be apparent that the prototype is not an implementation
   - For the UI, a sketch could be created using [Balsamiq](https://balsamiq.com/) or [Figma](https://www.figma.com/)
   - Use pseudonyms for test values
   - For presentation to the customer, a good sync between developer and sales should take place
