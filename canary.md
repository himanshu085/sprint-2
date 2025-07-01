# CD Design Document – Canary Deployment Strategy

![b715d6fb-b658-41c0-84be-167a7f182ddf](https://github.com/user-attachments/assets/7263866e-e3d2-46a1-bd56-21000e1176e8)

| **Author** | **Created on** | **Version** | **Last updated by** | **Last Edited On** | **Level**          | **Reviewer**       |
|------------|----------------|-------------|----------------------|---------------------|---------------------|---------------------|
| Himanshu   | 2025-07-01     | 1.0         | Himanshu             | 2025-07-01          | Internal Reviewer   | Siddharth Pawar     |
| Himanshu   | 2025-07-01     | 1.0         | Himanshu             | 2025-07-01          | L0                  | Imran               |
| Himanshu   | 2025-07-01     | 1.0         | Himanshu             | 2025-07-01          | L1                  | Shashi              |
| Himanshu   | 2025-07-01     | 1.0         | Himanshu             | 2025-07-01          | L2                  | Mahesh Kumar        |

## Table of Contents
- [Introduction](#introduction)  
- [Overview of Canary Deployment](#overview-of-canary-deployment)  
- [Process Flow](#process-flow)  
- [Step-by-Step Execution](#step-by-step-execution)  
- [Benefits](#benefits)  
- [Limitations](#limitations)  
- [When to Use](#when-to-use)  
- [Best Practices](#best-practices)  
- [Conclusion](#conclusion)  
- [Contact Information](#contact-information)  
- [References](#references)

## Introduction
This document explains the **Canary Deployment** strategy in the context of Continuous Delivery (CD). It covers the deployment flow, implementation steps, advantages, limitations, and usage guidelines to help engineering teams deploy new application versions safely and gradually.

## Overview of Canary Deployment
**Canary Deployment** is a technique used to reduce the risk of introducing a new software version into production by gradually rolling out the change to a small subset of users before a full release.

- Named after "canaries in coal mines"—early indicators of danger.  
- Ideal for testing real-world usage in production without exposing all users to the change.  
- Enables rollback with minimal impact if issues are detected early.

## Process Flow

1. Deploy the new version (canary) to a small percentage of production servers or users.  
2. Monitor for errors, performance issues, and metrics.  
3. If successful, gradually increase traffic to the new version.  
4. Fully promote the canary version or roll back if problems occur.

## Step-by-Step Execution

| Step | Description |
|------|-------------|
| **1. Prepare Environment** | Ensure production infrastructure supports traffic splitting (e.g., using a service mesh like Istio or AWS ALB routing rules). |
| **2. Deploy Canary Version** | Deploy the new version to a small subset (e.g., 5%) of instances or users. |
| **3. Redirect Partial Traffic** | Use feature flags, load balancer rules, or service mesh to send a fraction of traffic to the canary. |
| **4. Monitor and Validate** | Monitor logs, APM metrics (latency, error rates), and business KPIs. |
| **5. Gradual Rollout** | If healthy, incrementally increase traffic (e.g., 5% → 25% → 50% → 100%). |
| **6. Rollback If Needed** | If any anomaly is detected, route all traffic back to the stable version and redeploy if necessary. |
| **7. Full Deployment** | Upon success, promote the canary version as the main production version. |



![Screenshot from 2025-07-01 00-06-10](https://github.com/user-attachments/assets/d3bd1e81-c7b3-459c-bdf1-31a664a9ba0e)



As confidence grows, traffic is shifted from v1 to v2 until 100% is served by the canary version.


## Benefits

| Benefit | Description |
|--------|-------------|
| **Risk Mitigation** | Reduces the blast radius of bugs or failures. |
| **Real User Feedback** | Exposes changes to real traffic, validating production behavior. |
| **Incremental Release** | Allows staged rollouts for better control. |
| **Quick Rollback** | Easier to switch back when only a small portion is affected. |

## Limitations

| Limitation | Description |
|------------|-------------|
| **Infrastructure Complexity** | Requires advanced routing and observability tools. |
| **Traffic Segmentation** | May be challenging to segment traffic appropriately. |
| **Data Inconsistency** | Version mismatches can cause state or schema issues. |
| **Testing Overhead** | Requires strict monitoring and alert thresholds. |

## When to Use

Canary deployments are ideal when:

- You want to **test a new feature** in production without full exposure.  
- The application is **stateless** or supports backward-compatible updates.  
- You have **strong monitoring** and alerting systems in place.  
- **User experience is critical** and cannot tolerate wide-scale disruptions.

Avoid canary if:

- Your system lacks **dynamic traffic routing**.  
- You cannot easily **rollback** due to data/state issues.  
- You are releasing a **critical patch** that must be fully deployed instantly.

## Best Practices

- Use **feature flags** to control exposure.  
- Automate rollback based on error thresholds.  
- Monitor **SLOs** (Service Level Objectives) and **KPIs**.  
- Use **progressive rollout automation** (e.g., Flagger, Argo Rollouts).  
- Ensure **backward compatibility** in APIs and DB schemas.

## Conclusion

Canary deployment offers a safe and controlled mechanism to deploy new software versions in production. By minimizing exposure and validating in real-world conditions, teams can release confidently and respond quickly to regressions.

Choose canary deployment when risk mitigation, monitoring, and rollback agility are key to your deployment pipeline.

## Contact Information

| Name              | Email Address                                   |
|-------------------|--------------------------------------------------|
| Himanshu Parashar | himanshu.parashar.snaatak@mygurukulam.co         |

## References

| Resource | Description |
|----------|-------------|
| [Argo Rollouts](https://argo-rollouts.readthedocs.io) | Kubernetes controller for canary deployments |
| [LaunchDarkly](https://launchdarkly.com/) | Feature flag platform supporting canary releases |
| [AWS Canary Deployments](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html) | AWS CodeDeploy strategies |
| [Google SRE Book](https://sre.google/books/) | Service reliability and deployment strategies |
