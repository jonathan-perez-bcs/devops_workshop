![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
DKSH Opensource Software PaaS and DevOps
</div>

<div class="MCWHeader2">
Whiteboard design session student guide
</div>

<div class="MCWHeader3">
June 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

This scenario is fictional and will only be used for a non-production scenario.  Names and situations are borrowed for literary use.

© 2020 BCS Technology International Pty. Ltd.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

- [OSS PaaS and DevOps whiteboard design session student guide](#oss-paas-and-devops-whiteboard-design-session-student-guide)
  - [Abstract and learning objectives](#abstract-and-learning-objectives)
  - [Step 1: Review the customer case study](#step-1-review-the-customer-case-study)
    - [Customer situation](#customer-situation)
    - [Customer needs](#customer-needs)
    - [Customer objections](#customer-objections)
    - [Infographic for common scenarios](#infographic-for-common-scenarios)
  - [Step 2: Design a proof of concept solution](#step-2-design-a-proof-of-concept-solution)
  - [Step 3: Present the solution](#step-3-present-the-solution)
  - [Wrap-up](#wrap-up)
  - [Additional references](#additional-references)

# OSS PaaS and DevOps whiteboard design session student guide

## Abstract and learning objectives

In this whiteboard design session, you work with a group to design a solution for integrating and deploying complex open-source software (OSS) workloads into Azure PaaS. Your solution should handle the migration of an existing MERN (MongoDB, Express.js, React.js, Node.js) stack application. The application will be migrated from a hosted environment into Azure PaaS services, including migrating an existing MongoDB instance into Cosmos DB, enhancing application functionality using serverless technologies, and fully embracing modern DevOps tools.

At the end of this whiteboard design session, you will be better able to design solutions for migrating OSS applications into Azure PaaS using modern DevOps methodologies.

## Step 1: Review the customer case study

**Outcome**

Analyze your customer's needs.

Timeframe: 15 minutes

Directions:  With all participants in the session, the facilitator/SME presents an overview of the customer case study along with technical tips.

1. Meet your table participants and trainer.

2. Read all of the directions for steps 1-3 in the student guide.

3. As a table team, review the following customer case study.

### Customer situation

DKSH is the leading Market Expansion Services provider for companies who want to grow their business in Malaysia, serving customers in multiple countries.  Their Business Line Food and Beverage distributor has launched their highly-successful b2c e-commerce website, which sells subscriptions to their food ingredients supply service, in 2016, and have been steadily increasing their subscriber-base since. Their service caters to working professionals, who want convenient, reliable access to healthy meal choices, and pre-packaged recipes, without having to spend too much time preparing the meals. Customers can choose from a variety of meal plan options (e.g., vegetarian, vegan, gluten-free, high-protein), along with several options for portion sizes and the number of meals per week. Meals are delivered weekly directly to the customer's home.

Their current ingredients and meal plans include only dinner options. However, DKSH has received feedback from many customers expressing a desire for breakfast and lunch options to be included as part of the service offering. They would like to expand their meal services to meet this demand but feel they first need to address their rising infrastructure costs and management time. They have reached a point where managing their VM and server infrastructure is becoming a real challenge. They are interested in learning more about Platform as a Service (PaaS) solutions for OSS applications that could help them focus their expenditures and efforts on their core business rather than infrastructure. "We're finding that with every upgrade, we're spending more time and money on infrastructure and less on delivering the functionality and features that matter most to our customers," says Michael Chew, "and we need to rebalance those efforts." The development team at DKSH has some experience with Docker. It is interested in what options might be available for using containers to deploy their application into a cloud environment.

Their VP, Michael Chew, has voiced several concerns about migrating to the cloud. First, all of their business comes through their website, so high availability and performance are critically important to them, and she would like to see an improvement in this area as they migrate to the cloud. Second, she is a big proponent of open-source software (OSS) and would like to continue to use their open-source tools. Their web application uses the MERN stack (MongoDB, Express.js, React.JS, Node.js). They host their code in a private GitHub repository. A point of pride for DKSH has been their developers' involvement in the open-source community, with most members of the team frequently contributing to React.js on GitHub. They currently have a continuous integration workflow, triggered by each code check-in/commit in GitHub, using Jenkins.

Another feature she is interested in learning more about is identity management. Their existing web app requires users to register and log in before subscribing to a meal plan. Today, they handle this via a home-grown solution that stores usernames and passwords in the same database used for storing application information. They have experimented with other third-party solutions in the past, but found them difficult to integrate into their application, and are curious if moving their app into a cloud PaaS platform could help them integrate a better solution.

For their migration to the cloud, they have indicated that they would like to reuse as much code and architecture as possible. "We want the migration to be non-invasive. Although the existing code has its nuances and issues, we do not want to redesign the entire solution to migrate to the cloud. We want to be as efficient as possible with time and cost." Additionally, they want to continue using MongoDB APIs for data storage, to avoid having to rewrite application data access code, but don't want to worry about managing infrastructure, consistency, and replication.

The development team has also expressed that they would like to continue using GitHub as their code repository but is interested in improving upon their DevOps pipeline. They currently use Jenkins for their builds and are interested in any tools available in a cloud offering that could help with release management, or other aspects of a fully-integrated, modern DevOps pipeline. Ultimately, their goal is to automate and simplify deployments through CI/CD capabilities and deliver updates faster and more reliably.

They have also expressed interest in gaining a better understanding of how they can leverage serverless architecture to help their business grow. The development team has several processes that they are considering adding to their workflow, which they feel would be good candidates for a serverless approach, but are not sure which technologies and tools are right for the job. First, they would like to see if they can automate their daily order processing, queuing up the orders that need to go out each day, and updating their database when the orders have completed processing and shipped. Next, they would like to implement functionality to send customers an email or SMS text message when their credit card has been charged, and their weekly meal delivery has shipped.

DKSH is optimistic about the benefits of moving to a PaaS solution but very concerned about the time and potential changes that might be required to accommodate the transition for an OSS application.

### Customer needs

1. DKSH wants to migrate as much of their infrastructure as possible to the cloud to make it easier to take advantage of the scalability, reliability, and performance of a PaaS solution, and reduce the burden of building out and managing hardware and software.

2. They would like to reuse as much of their existing code and architecture as possible.

   - They want the migration to be non-invasive. Although the existing code has its nuances and issues, we do not want to redesign the entire solution to migrate to the cloud.
   - The would like to continue using MongoDB APIs for data storage, to avoid having to rewrite application data access code, but don't want to worry about managing infrastructure, consistency, replication, etc.

3. They want to continue to use their GitHub repository for source control, and Jenkins for their builds. However, they are interested in any value-added functionality available in Azure that might improve their ability to rapidly build, test, and deploy application updates through automated and simplified deployments using continuous integration/continuous delivery (CI/CD) capabilities.

4. Want to maintain a dedication to open source technologies, and maintain those same technologies within the cloud solution, while taking advantage of integrations with the cloud environment, where possible.

5. Looking for opportunities to integrate automated, serverless processes, specifically around their order processing and SMS notifications to customers.

6. Desire a replacement solution for safeguarding and managing user identities.

7. DKSH offers thousands of different meal options, but currently doesn't have an easy way for customers to search for specific meals or types of meals. They would like to add search capabilities to their application, providing the ability for customers to more easily find meals or options.

### Customer objections

1. Microsoft isn't known for supporting open source. Is Azure really an appropriate platform for hosting an OSS application using PaaS?

2. We're interested in using containers, but we're not sure how they work in Azure. Does Azure provide reliable ways to deploy and manage containers? What is the simplest way to move containers to Azure, based on our PaaS experience, while at the same time considering our scale and growth requirements?

3. We want to improve our current DevOps workflow. What options are available in Azure? Can we implement a CI/CD pipeline? Can we continue to use Jenkins? Does Azure offer any value-added services which we can leverage in our existing Jenkins CI pipeline?

4. We've heard about Azure Active Directory B2C (Azure AD B2C) to manage application users, but we are not sure how that would work with our open-source application.

5. Is Azure Cognitive Search an appropriate solution for improving the search capabilities of our OSS app?

6. We no longer want to maintain VMs for running our MongoDB database. Does Azure offer a solution that will allow us to continue using the MongoDB APIs while benefiting from the scalability and reliability of a PaaS database platform?

7. We would like to understand more about the benefits of a serverless architecture. In Azure, does it mean only using Azure Functions, or is there more to it?

8. We've read that Visual Studio Code is a free, open-source code editor that can be used for OSS development. Can our developers continue to use their IDE, or do they need to switch over to using Visual Studio Code to write code destined for the Azure platform? Does Visual Studio Code offer any features or integration capabilities that would make it advantageous over a non-Microsoft code editor?

### Infographic for common scenarios

![This data flow diagram illustrates how to build highly scalable e-commerce websites with catalog, checkout, analysis, and forecasting. Fifteen components in this diagram interact with each other between end-users and the enterprise, and the components are organized in three tiers: the internet tier, the services tier, and the data tier.](media/image2.png "Common E-Commerce Website scenarios infographic")

## Step 2: Design a proof of concept solution

**Outcome**

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 60 minutes

**Business needs**

Directions: With all participants at your table, answer the following questions and list the answers on a flip chart:

1. Who should you present this solution to? Who is your target customer audience? Who are the decision makers?

2. What customer business needs do you need to address with your solution?

**Design**

Directions: With all participants at your table, respond to the following questions on a flip chart:

*High-level architecture*

1. Without getting into the details (the following sections address the particulars), diagram your initial vision for handling the top-level requirements for the OSS app and migration, serverless architecture integration, search integration, Azure AD B2C implementation, and DevOps pipeline. You will refine this diagram as you proceed.

*PaaS solution*

1. What PaaS solution would you propose to DKSH for moving their application into Azure? Will this solution minimize the number of application code changes required to migrate the application? How will container orchestration be handled?

2. Describe the scalability, high-availability, and performance options that are open to Best For Your Organics Company with the PaaS solution you proposed above.

3. What options does the customer have for a Docker image registry? Which option would you recommend?

*Database migration*

1. What service would you recommend for hosting the customer's MongoDB in Azure, and ensuring they can continue to use the MongoDB API for accessing their data?

2. What application changes need to be made to accommodate using a Cosmos DB database with MongoDB API? Be specific about the impact of the change on their application code.

3. How would you handle importing their existing data into Azure Cosmos DB? What factors do you need to consider when doing the import?

*Serverless architecture*

1. What serverless technologies would you recommend DKSH use for automating their order processing?

2. How would you recommend the customer handle notifying customers that their order has been processed? Are there specific Azure services that can be used?

*Identity management*

1. How would you recommend DKSH implement identity management in their customer-facing application? Be specific about both the implementation and process you would use to gain DKSH's acceptance of the proposed solution.

*Search integration*

1. How could Azure Cognitive Search be integrated into the OSS application?

*DevOps workflows*

1. How can Jenkins be used to help the customer create a full CI/CD pipeline?

**Prepare**

Directions: With all participants:

1. Identify any customer needs that are not addressed with the proposed solution.

2. Identify the benefits of your solution.

3. Determine how you will respond to the customer's objections.

Prepare a 15-minute chalk-talk style presentation to the customer.

## Step 3: Present the solution

**Outcome**

Present a solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 30 minutes

**Presentation**

Directions:

1. Prepare to present online.  (take snapshots with your camera / phone and upload to your pc to present).  

2. One team is the Microsoft team and the other will be the customer team

3. The Microsoft team will present their proposed solution to the customer.

4. The customer makes one of the objections from the list of objections.

5. The Microsoft team responds to the objection.

6. The customer team gives feedback to the Microsoft team.

7. The Microsoft team and customer team switch roles and repeat Steps 2-6.

## Wrap-up

Timeframe: 15 minutes

Directions: BCS shares the preferred solution for the case study.

## Additional references

|    |            |
|----------|-------------|
| **Description** | **Links** |
| Azure Cosmos DB API for MongoDB | <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction/> |
| Migrate MongoDB to Azure Cosmos DB's API for MongoDB online using DMS | <https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db-online> |
| Migrate MongoDB to Azure Cosmos DB's API for MongoDB offline using DMS | <https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db?toc=/azure/cosmos-db/toc.json> |
| Azure Container Registry | <https://azure.microsoft.comservices/container-registry> |
| Azure functions | <https://docs.microsoft.com/azure/azure-functions> |
| Logic Apps | <https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps> |
| Azure AD B2C | <https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-overview> |
| Cosmos DB | <https://docs.microsoft.com/azure/cosmos-db> |
| Deploy to Azure App Service using Jenkins plugin | <https://docs.microsoft.com/azure/jenkins/deploy-jenkins-app-service-plugin> |
| Create Jenkins server in Azure | <https://docs.microsoft.com/en-us/azure/jenkins/install-jenkins-solution-template> |
| Azure Cognitive Search in Node.js | <https://docs.microsoft.com/azure/search/search-get-started-nodejs> |
| Visual Studio (VS) Code for OSS | <https://code.visualstudio.com/docs/nodejs/reactjs-tutorial> |
| Web App for containers | <https://azure.microsoft.com/blog/webapp-for-containers-overview/> |
