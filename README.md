[![Build Status](https://github.com/DependencyTrack/dependency-track/actions/workflows/ci-build.yaml/badge.svg)](https://github.com/DependencyTrack/dependency-track/actions?workflow=CI+Build)
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/b2ecd06dab57438a9a55bc4a71c5a8ce)](https://www.codacy.com/gh/DependencyTrack/dependency-track/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=DependencyTrack/dependency-track&amp;utm_campaign=Badge_Grade)
[![Alpine](https://img.shields.io/badge/built%20on-Alpine-blue.svg)](https://github.com/stevespringett/Alpine)
[![OWASP Flagship](https://img.shields.io/badge/owasp-flagship%20project-orange.svg)](https://www.owasp.org/index.php/OWASP_Dependency_Track_Project)
[![Website](https://img.shields.io/badge/https://-dependencytrack.org-blue.svg)](https://dependencytrack.org/)
[![Documentation](https://img.shields.io/badge/read-documentation-blue.svg)](https://docs.dependencytrack.org/)
[![Slack](https://img.shields.io/badge/chat%20on-slack-46BC99.svg)](https://dependencytrack.org/slack)
[![Group Discussion](https://img.shields.io/badge/discussion-groups.io-blue.svg)](https://dependencytrack.org/discussion)
[![YouTube Subscribe](https://img.shields.io/badge/youtube-subscribe-%23c4302b.svg)](https://dependencytrack.org/youtube)
[![Twitter](https://img.shields.io/twitter/follow/dependencytrack.svg?label=Follow&style=social)](https://twitter.com/dependencytrack)
[![Downloads](https://img.shields.io/github/downloads/DependencyTrack/dependency-track/total.svg)](https://github.com/DependencyTrack/dependency-track/releases)
[![Latest](https://img.shields.io/github/release/DependencyTrack/dependency-track.svg)](https://github.com/DependencyTrack/dependency-track/releases)
[![Pulls - API Server](https://img.shields.io/docker/pulls/dependencytrack/apiserver.svg?label=Docker%20Pulls%20%28API%20Server%29)](https://hub.docker.com/r/dependencytrack/apiserver/)
[![Pulls - Frontend](https://img.shields.io/docker/pulls/dependencytrack/frontend.svg?label=Docker%20Pulls%20%28Frontend%29)](https://hub.docker.com/r/dependencytrack/frontend/)
[![Pulls - Bundled](https://img.shields.io/docker/pulls/dependencytrack/bundled.svg?label=Docker%20Pulls%20%28Bundled%29)](https://hub.docker.com/r/dependencytrack/bundled/)
[![Pulls - Legacy](https://img.shields.io/docker/pulls/owasp/dependency-track.svg?label=Docker%20Pulls%20%28OWASP%20Legacy%29)](https://hub.docker.com/r/owasp/dependency-track/)

![logo preview](https://raw.githubusercontent.com/DependencyTrack/branding/master/dt-logo.svg?sanitize=true)


For the offical repository, please refer to: https://github.com/DependencyTrack/dependency-track

Dependency-Track is an intelligent [Component Analysis] platform that allows organizations to
identify and reduce risk in the software supply chain. Dependency-Track takes a unique
and highly beneficial approach by leveraging the capabilities of [Software Bill of Materials] (SBOM). This approach
provides capabilities that traditional Software Composition Analysis (SCA) solutions cannot achieve.

Dependency-Track monitors component usage across all versions of every application in its portfolio in order to
proactively identify risk across an organization. The platform has an API-first design and is ideal for use in
CI/CD environments.

## Ecosystem Overview
![alt text](./docs/images/integrations.png)

## Features
* Consumes and produces [CycloneDX] Software Bill of Materials (SBOM)
* Consumes and produces [CycloneDX Vulnerability Exploitability Exchange (VEX)](https://cyclonedx.org/capabilities/vex/)
* Component support for:
  * Applications
  * Libraries
  * Frameworks
  * Operating systems
  * Containers
  * Firmware
  * Files
  * Hardware
  * Services
* Tracks component usage across every application in an organizations portfolio
* Quickly identify what is affected, and where
* Identifies multiple forms of risk including
  * Components with known vulnerabilities
  * Out-of-date components
  * Modified components
  * License risk
  * More coming soon...
* Integrates with multiple sources of vulnerability intelligence including:
  * [National Vulnerability Database] (NVD)
  * [GitHub Advisories]
  * [Sonatype OSS Index]
  * [Snyk]
  * [Trivy]
  * [OSV]
  * [VulnDB] from [Risk Based Security]
  * More coming soon.
* Helps to prioritize mitigation by incorporating support for the [Exploit Prediction Scoring System (EPSS)](https://www.first.org/epss/)
* Maintain a private vulnerability database of vulnerability components
* Robust policy engine with support for global and per-project policies
  * Security risk and compliance
  * License risk and compliance
  * Operational risk and compliance
* Ecosystem agnostic with built-in repository support for:
  * Cargo (Rust)
  * Composer (PHP)
  * Gems (Ruby)
  * Hex (Erlang/Elixir)
  * Maven (Java)
  * NPM (Javascript)
  * CPAN (Perl)
  * NuGet (.NET)
  * PyPI (Python)
  * More coming soon.
* Identifies APIs and external service components including:
  * Service provider
  * Endpoint URIs
  * Data classification
  * Directional flow of data
  * Trust boundary traversal
  * Authentication requirements
* Includes a comprehensive auditing workflow for triaging results
* Configurable notifications supporting Slack, Microsoft Teams, Mattermost, Webhooks, Webex, Email and Jira
* Supports standardized SPDX license ID’s and tracks license use by component
* Easy to read metrics for components, projects, and portfolio
* Native support for Kenna Security, Fortify SSC, ThreadFix, and DefectDojo
* API-first design facilitates easy integration with other systems
* API documentation available in OpenAPI format
* OAuth 2.0 + OpenID Connect (OIDC) support for single sign-on (authN/authZ)
* Supports internally managed users, Active Directory/LDAP, and API Keys
* Simple to install and configure. Get up and running in just a few minutes

<hr>
  

## Difference from the base repository

This specific project runs with a custom github action script as it does the following.
- It creates a docker image of this repository and deploys it to Amazon ECR.
- Checks if there is a valid ECR image of this repository here: https://github.com/JoesphK/Container-DT-Frontend . The machine auto creation process fails otherwise.
- If successful, it creates an EC2 instance, pulls both images and configures the application for you.

---  

## Additonal features
- Easy of Deploy.  
- Minimal input. Just define your AWS user credentials in the secrets and attach it to the project.  
- Creates test machines for you to test your changes every time the script runs.
- You can cancel the run of the custom machine or call it manually at any time.
- Supports deployment over and ArgoCD.
---     
## How to use
- Using the test machines way:
  - simply ensure you have an ECR image of this project here: https://github.com/JoesphK/Container-DT-Frontend .
  - Change the environment variables to be your AWS account and your own credentials.
  - Whenever you are ready, click run the script and wait.
  - Once done, open the machine on HTTP://<PUBLIC-IP>
- Using the EKS cluster + ArgoCD
  - Use this repository instead: https://github.com/JoesphK/Dependency-Track-ArgoCD-edition
