---
layout: single
title: "Instant rollback is a myth in most systems."
date: 2025-11-26
categories: cloud devops finops
tags: [aws, gcp, kubernetes, terraform, devops, finops, cicd, automation, cloud, scaling, resilience, spot]
author_profile: true
---

I've learned this managing high-throughput services where the textbook comparison between Blue/Green and Rolling updates fails. The discussion almost always misses the most critical component: state.

A rolling update is resource-efficient, but it creates a transient period where old and new code run concurrently. I've spent days debugging subtle, non-deterministic failures caused by this mixed state, from API contract drift to inconsistent session handling.

Blue/Green promises a clean cutover. But its cost isn't just doubling your compute. The real challenge is managing shared dependencies like a database. If your new "green" environment has already written data with an evolved schema, your "blue" environment can't simply take over again. Your rollback path is already compromised.

The choice isn't just speed vs. safety. It's about managing risk for a specific type of change.

1. For stateless services with backward-compatible changes, a rolling update is pragmatic.
2. For breaking changes or stateful services, I require a Blue/Green deployment coupled with a rigorously tested data migration and rollback strategy.

How do you handle database schema evolution for zero-downtime Blue/Green deployments? What's your playbook when the data has already been changed?

#BlueGreenDeployment #RollingUpdate #DeploymentStrategy #CI #CD #ContinuousDelivery #ContinuousDeployment #DevOps #SRE #SiteReliabilityEngineering #HighAvailability #ZeroDowntime #SystemDesign #CloudArchitecture #SoftwareArchitecture #DistributedSystems #AWS #Azure #GCP #Kubernetes #K8s #InfrastructureAsCode #PrincipalEngineer #StaffEngineer #CloudArchitect #SoftwareEngineer #TechLead
