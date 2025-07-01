# Canary Deployment Strategy Documentation

![Canary Deployment](https://github.com/user-attachments/assets/5cf6a5d5-421f-4d54-aeab-ad8b59c50213)

| Author           | Created on | Version   | Last updated by   | Last edited on | Reviewer        |
|------------------|------------|-----------|--------------------|----------------|-----------------|
| Prashant Sharma  | 07-04-25   | Version 1 | Prashant Sharma    | 07-04-25       | Siddharth Pawar |
| Prashant Sharma  | 07-04-25   | Version 2 | Prashant Sharma    | 11-04-25       | Mukul Joshi     |
| Prashant Sharma  | 07-04-25   | Version 3 | Prashant Sharma    | 16-04-25       | Piyush Upadhyay |

---

## Table of Contents

1. [Introduction](#introduction)  
2. [What is Canary Deployment](#what-is-canary-deployment)  
3. [Flow Diagram](#flow-diagram)  
4. [Stages of Canary Deployment](#stages-of-canary-deployment)  
5. [Benefits of Canary Deployment](#benefits-of-canary-deployment)  
6. [Advantages](#advantages)  
7. [Disadvantages](#disadvantages)  
8. [Best Practices](#best-practices)  
9. [Conclusion](#conclusion)  
10. [References](#references)  
11. [Contact Information](#contact-information)  

---

## Introduction

Canary deployment is a strategy that makes app releases smoother and less prone to bugs. By rolling out updates slowly, it allows developers to catch any issues early, ensuring users have a seamless and trouble-free experience.

---

## What is Canary Deployment

- Canary deployment is a software release strategy where a new version of an application is rolled out to a small, controlled subset of users first (the "canaries"), before being gradually released to the entire user base.

- Think of it like testing a new feature or update on a small group of users to see how it performs before making it available to everyone. If everything goes well, the update is rolled out to more users. If any bugs or issues arise, they can be fixed without affecting the whole user base.

![Canary Deployment Explanation](https://github.com/user-attachments/assets/b1e2334f-fce1-4275-b690-56965597b477)

---

## Flow Diagram

Canary release is a deployment rollout strategy that aims at minimizing new software risks by directing a small percentage of users to the new version of the application. After verifying that the new application works as intended, the traffic directed to it is gradually increased and eventually, all traffic is directed to it. In case an issue is detected at any point throughout the deployment, a rollback is performed with ease because both the current and the new versions are in the production environment.

![Flow Diagram](https://github.com/user-attachments/assets/aecbdea7-054c-499f-bb7d-17ec85d1c319)

---

## Stages of Canary Deployment

| **Stage**           | **Description**                                                                                                          |
|---------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Plan and Create** | A new canary setup is created where the latest update is tested. A small portion of user traffic is directed to the new version, while the majority continue using the old version. |
| **Analyze**         | Data is collected from users interacting with the canary version. Metrics, logs, and performance data are analyzed and compared to the old version to identify any issues. |
| **Roll**            | After analysis, the team decides whether to fully release the update to all users or revert to the old version to address issues found during testing. |

---

## Benefits of Canary Deployment

| **Benefit**                         | **Description**                                                                                             |
|------------------------------------|-------------------------------------------------------------------------------------------------------------|
| **Better Control Over Feature Releases** | Allows identification and fixing of mistakes without affecting many users.                                   |
| **Real-World Testing**             | Enables testing new updates with real users in a controlled way.                                             |
| **No Downtime & Easy Rollback**    | Quickly revert changes if problems arise.                                                                   |
| **Lower Costs with Small Infrastructure** | Reduces need for large-scale resources during testing.                                                       |
| **Flexibility to Test New Features** | Developers can experiment with less risk.                                                                   |

---

## Advantages

| **Advantage**               | **Description**                                                         |
|-----------------------------|-------------------------------------------------------------------------|
| **Lower Risk**              | Updates tested with a small group first.                                |
| **Early Problem Detection** | Fix issues before they affect the full user base.                       |
| **Quick Rollback**          | Easy to undo changes if something goes wrong.                           |
| **Faster Innovation**       | Enables quicker testing and iteration of new features.                  |
| **Better Performance Checks** | Identify performance issues early.                                     |

---

## Disadvantages

| **Disadvantage**            | **Description**                                                         |
|-----------------------------|-------------------------------------------------------------------------|
| **Difficult Setup**         | Requires careful planning and configuration.                           |
| **Limited Feedback**        | Smaller user sample might not catch all issues.                        |
| **Slower Updates**          | Gradual rollout means slower delivery to the full user base.           |
| **Needs Strong Monitoring** | Requires ongoing performance and stability checks.                     |

---

## Best Practices

| **Best Practice**              | **Description**                                                                 |
|-------------------------------|---------------------------------------------------------------------------------|
| **Automate Traffic Shifting** | Use CI/CD pipelines to automate and control canary rollouts.                   |
| **Define Clear Metrics**      | Pre-define KPIs to monitor deployment success or failure.                     |
| **Use Feature Flags**         | Decouple feature deployment from code deployment.                             |
| **Enable Rollback Mechanisms**| Implement automated rollback based on performance triggers or errors.          |

---

## Conclusion

Canary deployment is a reliable, low-risk method for introducing new software changes. When implemented with proper planning, automation, and observability, it empowers teams to move fast without compromising stability.

---

## References

| Title                          | Link                                                                                         |
|--------------------------------|----------------------------------------------------------------------------------------------|
| Deployment Strategies          | [Deployment Strategies - APWide](https://www.apwide.com/8-deployment-strategies-explained-and-compared/) |
| Canary Deployment Strategy     | [Semaphore Blog](https://semaphore.io/blog/what-is-canary-deployment)                        |

---

## Contact Information

| Name            | Email                                |
|-----------------|----------------------------------------|
| Prashant Sharma | prashant.sharma@mygurukulam.co        |
