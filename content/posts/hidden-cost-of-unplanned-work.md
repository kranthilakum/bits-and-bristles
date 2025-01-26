---
title: "The Hidden Costs of Unplanned Work: Balancing Urgency and Technical Realities in Software Teams"
date: 2025-01-26T09:55:46+05:30
draft: false
categories:
  - "software development"
  - "devops"
  - "agile practices"
  - "team management"
  - "tech culture"
tags:
  - "unplanned work"
  - "work-life balance"
  - "technical-debt"
---

In the fast-paced world of software development, teams are often thrust into high-pressure situations where urgency collides with technical constraints. A recent scenario involving a development team, a DevOps team, and a critical demo for a prospective customer reveals the hidden costs of unplanned work—especially when business urgency dictates priorities. This situation underscores the complexities of handling urgent issues, balancing technical challenges, and managing team stress, while also highlighting the importance of realistic expectations and role clarity.

The scenario begins on Thursday night when the QA manager informs the development team about the sales team's scheduled demo with a prospective customer on Monday and that the app must be thoroughly tested, and any issues that arise should be resolved as quickly as possible. However, the demo is scheduled to take place in a demo environment—one that the development team has never used for testing.

The development team already has multiple priorities, including supporting existing customers, improving the app in general, and ensuring its stability across various environments, the demo environment was never a focal point. Their attention was naturally directed toward the primary production environment and the needs of their current user base. As a result, the demo environment—being an isolated setup with different configurations—was not considered during their regular testing or development cycles.

By Friday afternoon, the QA engineer identifies a critical issue in the demo environment: the app fails to load, returning a 503 service unavailable error. The issue is immediately flagged as a blocker and escalated to the DevOps team, with the QA team raising the ticket. The development team checks the app's services in Rancher—the service management tool—and confirms that all services are running correctly. They execute basic tests, triggering `curl` commands to the services, which return responses. However, the request from the app to the services still results in a 503 error.

The manager, aware of the technical challenges, suggests to the developer that the issue might be related to service configuration. While the developer is unable to resolve it, he checks the list of running services and confirms that everything is operational at the service level. Still, the app fails to make a successful request to the services, and the error persists.

After five hours of investigation, the developer consults with an architect, who ultimately deduces that the problem lies in a misconfiguration at the platform level. However, the DevOps team, particularly the DevOps engineer, remains reluctant to accept the diagnosis and continues to resist the conclusion, suggesting that the issue lies with the app itself. As the situation stretches into Friday evening, the DevOps team reluctantly consults a specialist, who ultimately concurs with the architect’s analysis and uncovers additional platform-level issues.

By Friday evening at 7 PM, with no resolution in sight, the DevOps engineer adds a comment to the blocker ticket, stating that he’s attempted a few solutions but has not yet resolved the issue. He then signs off for the weekend, stating he’ll revisit the issue on Monday. The developer and the QA team also sign off for the day, and by Friday night, the problem remains unresolved.

At 3 AM on Sunday, the manager pings the developer directly in a personal Teams message, urging immediate action. He adds a comment to the blocker ticket, tagging both the DevOps and development teams, stressing that the issue “**can’t wait until Monday**.” The manager, while aware of the technical challenges, is under the assumption that this can be fixed immediately, disregarding the complexities involved.

The developer, recognizing the pressure but also understanding the boundaries of their role, intentionally ignores the comment on the ticket. The ticket was never assigned to him, and the issue falls outside his area of expertise—especially since the issue is related to platform-level configuration, something the developer has no access to or authority over. Instead, the developer responds to the manager's personal message at 10 AM, pointing out that the issue and its resolution are within the domain of the DevOps team. He reminds the manager that a ticket has already been assigned to the DevOps team and that the DevOps engineer has the necessary expertise to address the platform misconfiguration.

The developer, limited by access and authority, cannot resolve the issue himself. He does not have the expertise or control over the demo environment, nor does he have the mandate to push the DevOps engineer to work over the weekend. With the developer's response, the responsibility is again shifted back to the DevOps team.

This situation illustrates a critical point: **unplanned work—particularly work that stems from external business needs—can impose serious stress on tech teams, disrupt workflow, and compromise quality**. In this case, the sales team’s scheduled demo created an urgency that trickled down to the development and DevOps teams. But without an understanding of the technical complexity, the pressure to resolve the issue immediately was placed on the wrong shoulders.

The pressure to deliver without fully understanding the root causes often leads to **firefighting rather than sustainable problem-solving**. This unplanned work, often thrust upon the development and DevOps teams, forces them to abandon planned tasks, disrupts their flow, and leads to frustration. The situation is exacerbated by the manager’s decision to push for an immediate resolution without understanding that certain issues—like platform misconfigurations—require a level of expertise and access that the development team simply doesn’t have.

The long-term implications of such unplanned work extend beyond the immediate technical challenges. When teams are repeatedly tasked with urgent requests, often outside regular working hours, the mental load increases, and work-life balance deteriorates. This constant need to be on-call can lead to burnout, frustration, and a sense of powerlessness when team members feel they have no control over their work environment or their priorities.

It’s important for teams to acknowledge that while urgency is a constant in many businesses, it should not come at the cost of sustainability or employee well-being. Developers and DevOps engineers may have the technical expertise to solve problems, but they cannot resolve issues without the necessary tools, access, or support. By continuing to push for immediate results without addressing these constraints, businesses risk burning out their teams and lowering the quality of their work.

To avoid these kinds of situations, **clearer communication is essential**. Sales, product, and management teams need to develop a deeper understanding of the technical limitations and constraints the development and DevOps teams face. With a better understanding of the complexities involved in technical tasks, business stakeholders can set more realistic expectations.

Managers should respect the boundaries of each role. In this case, the development team is responsible for building and testing the app, but platform-level misconfigurations fall under the responsibility of the DevOps team. When urgency arises, it’s crucial to allow the teams to address the issues within their areas of expertise, rather than overloading them with tasks outside their control.

This case highlights the hidden costs of unplanned work—work that emerges due to external pressures and creates a constant sense of urgency. When expectations are misaligned with technical realities, it creates unnecessary stress, disrupts team productivity, and threatens work-life balance. The solution lies in fostering better communication between business and technical teams, setting realistic expectations, and allowing teams the space to work at a sustainable pace. By respecting the expertise and limitations of each role, organizations can avoid creating a culture of constant firefighting and ensure long-term success without compromising team well-being or quality.
