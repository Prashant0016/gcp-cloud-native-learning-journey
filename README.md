# Google Cloud Platform (GCP) Cloud-Native Learning Journey

> A hands-on collection of Google Cloud Platform (GCP) labs covering cloud fundamentals, networking, containers, Kubernetes, Infrastructure as Code, CI/CD, serverless computing, observability, and cloud-native application deployment.

## Project Overview

This repository documents my hands-on learning journey through Google Cloud Platform while exploring modern cloud-native technologies and deployment practices.
The project consists of **25 practical labs**, each focusing on a specific cloud concept, beginning with basic Compute Engine deployments and progressing toward enterprise-grade Kubernetes workloads, Infrastructure as Code, CI/CD pipelines, event-driven architectures, and complete cloud-native application deployment.

> Sandbox Used : Pluralsight

Every task includes:

- Detailed implementation steps
- Concept explanations
- Commands used
- YAML/Terraform configurations (where applicable)
- Screenshots (where applicable)
- Key takeaways

The objective was not simply to complete labs, but to understand **how real production systems are designed, deployed, monitored, secured, and maintained in Google Cloud**.

## Repository Highlights

- 25 hands-on Google Cloud labs
- Step-by-step screenshots for every task
- Detailed README for each lab
- Consolidated study notes for quick revision
- Covers Docker, Kubernetes, Terraform, Cloud Run, Pub/Sub, Helm, CI/CD, IAM, Networking, Monitoring, and more
- Designed as both a learning portfolio and interview revision resource

# Quick Reference Notes

Alongside the detailed task documentation, this repository also includes a consolidated set of personal study notes created while performing the hands-on labs.
These notes summarize important concepts, commands, and observations from the learning journey in a single document, making them useful for quick revision before interviews, certification preparation, or refreshing cloud-native concepts.

**Included documents**

- 📄**GCP Cloud-Native Learning Notes.pdf** *(Quick revision guide covering all 25 tasks - PDF )*
- 📄 **GCP Cloud-Native Learning Notes.docx** *(Quick revision guide covering all 25 tasks - WORD)*

If you're looking for a concise overview instead of the step-by-step walkthroughs, this document is a good place to start.

> **Note:** The PDF/Word document is intended as a revision companion. For implementation details, explanations, YAML files, Terraform configurations, and screenshots, refer to the individual task folders. These notes were written manually for personal reference and may contain minor editorial/typographical/formatting inconsistencies. The emphasis is on the technical content rather than the presentation.

# Learning Objectives

Throughout this project I explored:

- Google Cloud fundamentals
- Virtual Machines
- Cloud Networking
- Docker & Containerization
- Artifact Registry
- Google Kubernetes Engine (GKE)
- Kubernetes Networking
- ConfigMaps & Secrets
- Persistent Storage
- Ingress
- Rolling Updates & Rollbacks
- Namespaces
- Resource Management
- Horizontal Pod Autoscaling (HPA)
- Helm
- Infrastructure as Code using Terraform
- Cloud Run
- Cloud Build
- Cloud Logging & Monitoring
- Google Cloud Pub/Sub
- End-to-End Cloud Native Architecture

# Repository Structure

```
├── Task 01 - Compute Engine
├── Task 02 - Cloud Storage
├── Task 03 - IAM
├── Task 04 - VPC Networking
├── Task 05 - Docker Fundamentals
├── Task 06 - Custom Docker Images
├── Task 07 - Kubernetes Fundamentals
├── Task 08 - Cloud Run
├── Task 09 - Cloud Logging & Monitoring
├── Task 10 - Cloud Build (CI/CD)
├── Task 11 - Terraform Basics
├── Task 12 - Kubernetes Workloads
├── Task 13 - Kubernetes Services
├── Task 14 - ConfigMaps & Secrets
├── Task 15 - Persistent Storage
├── Task 16 - Kubernetes Ingress
├── Task 17 - CI/CD for Kubernetes
├── Task 18 - Rolling Updates & Rollbacks
├── Task 19 - Namespaces
├── Task 20 - Resource Requests & Quotas
├── Task 21 - Horizontal Pod Autoscaler
├── Task 22 - Helm
├── Task 23 - Terraform Fundamentals
├── Task 24 - Google Cloud Pub/Sub
└── Task 25 - End-to-End Cloud Native Application

```
Each folder contains:

- README.md
- Supporting configuration files (where applicable)
- Screenshots (where applicable)

# Technologies & Services Covered

## Google Cloud Platform

- Compute Engine
- Cloud Storage
- IAM
- VPC
- Firewall Rules
- Cloud Run
- Artifact Registry
- Cloud Build
- Cloud Logging
- Cloud Monitoring
- Pub/Sub
- Google Kubernetes Engine (GKE)

## Containers

- Docker
- Docker Images
- Dockerfiles
- Container Registry Concepts

## Kubernetes

- Pods
- Deployments
- Services
- Ingress
- ConfigMaps
- Secrets
- Persistent Volumes
- Persistent Volume Claims
- Namespaces
- Resource Quotas
- Autoscaling
- Rolling Updates
- Rollbacks
- Helm

## Infrastructure as Code

- Terraform
- Providers
- Resources
- State Management
- Infrastructure Provisioning

# Skills Practiced

Through these labs I gained practical experience with:

- Deploying cloud infrastructure
- Managing Linux virtual machines
- Designing secure cloud networking
- Building Docker images
- Running containerized workloads
- Deploying applications to Kubernetes
- Scaling workloads
- Managing Kubernetes networking
- Managing application configuration
- Persistent storage in Kubernetes
- CI/CD concepts
- Infrastructure as Code
- Event-driven architectures
- Cloud monitoring and troubleshooting
- Cloud-native application deployment

# Learning Progress

The learning path followed a gradual progression:

| Phase | Topics |
|-------|--------|
| Cloud Fundamentals | Compute Engine, Storage, IAM |
| Networking | VPC, Firewall Rules |
| Containers | Docker, Images, Dockerfiles |
| Kubernetes | Deployments, Services, Scaling |
| Advanced Kubernetes | Ingress, ConfigMaps, Secrets, Storage |
| DevOps | CI/CD, Cloud Build, Helm |
| Infrastructure | Terraform |
| Serverless | Cloud Run |
| Observability | Logging & Monitoring |
| Event-Driven Systems | Pub/Sub |
| Capstone | Complete Cloud-Native Deployment |

# Prerequisites

To reproduce these labs you should have:

- Google Cloud Account
- Google Cloud Project
- Basic Linux knowledge
- Cloud Shell access
- kubectl
- Terraform
- Docker
- Helm

Most labs were performed inside **Google Cloud Skills Boost / sandbox environments**, so some IAM permissions and resource quotas were intentionally restricted.

# Notes

Some labs encountered expected sandbox limitations, including:

- Restricted IAM permissions
- Resource quotas
- Dynamic storage provisioning restrictions
- Limited logging permissions
- Temporary project environments

Where applicable, these observations have been documented in the individual task READMEs.

# Project Highlights

✔ 25 Hands-on Labs

✔ 100+ Cloud Commands Practiced

✔ Kubernetes Administration

✔ Docker & Containerization

✔ Infrastructure as Code

✔ Cloud Networking

✔ CI/CD Concepts

✔ Event-Driven Architecture

✔ Cloud-Native Deployment

✔ Production-Oriented Concepts

# About This Repository

This repository serves as my personal cloud-native learning portfolio and documents the practical knowledge gained while exploring Google Cloud Platform.
Rather than focusing only on theory, every concept was reinforced through hands-on implementation and documented with detailed explanations and screenshots.

## About Me

I am a Computer Science graduate with an interest in **Cloud Computing**, **Cloud-Native Development**, **Google Cloud Platform**, **Kubernetes**, **Docker**, **Infrastructure as Code**, and **DevOps**.
This repository represents an important milestone in my journey toward becoming a Cloud Native Developer.

## Disclaimer

This repository is intended for educational purposes.
Some configurations have been simplified to suit sandbox learning environments and may differ from production implementations.

## Acknowledgements

This project was completed through extensive hands-on practice using Google Cloud Platform and cloud-native technologies while documenting each concept to reinforce practical understanding.
