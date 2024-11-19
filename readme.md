https://commbank.sharepoint.com/sites/onecba-engineering/SitePages/Applicants.aspx

## Provide links as evidence to the body of work, portfolio or other suitable artefacts (ie Github repo's, design documents etc).

### Github repo:
https://github.source.internal.cba/liul31 (227 contributions in the last year)
https://github.com/Lucas-Liu_cba (287 contributions)

### Website
https://llcode.tech

## a) What product/s do you work on and what is your role in that product's development?
I am currently doing work across two different squads.

One of the product I am involved with is the publishing and orchestration framework. This framework is crucial for managing the execution, transformation, and loading of model outputs. My role involves developing and maintaining this framework to ensure it meets the functional requirements as outlined in our user stories. Specifically, I focus on automating model job executions, transforming model outputs, and ensuring data quality through various validation checks. My key contributions are:

* Performed airflow strategic alert uplift image testing, by ensuring All existing flows are validated with new docker image.
* Built and pushed a custom Airflow Docker image with the updated Amazon provider package to Artifactory, then test it in the non-production environment to ensure all existing DAGs remain functional and resolve the `GlueSensorOperator` error.
* Created and configure the FRAUMD Kafka publisher and streamer pipeline in the adc-fraumd-stg namespace, then perform a full end-to-end test, including Helm charts creation, secrets management, and a complete test run from Snowflake to Oracle CEE.
 
As part of maintaining and building the publishing and orchestration framework, we also utilised a tool called apache airflow which is a workflow management application that can perform dynamic workflow creation and scheduling and monitoring tasks. An Airflow DAG (Directed Acyclic Graph) is a collection of tasks organised in a way that reflects their dependencies and execution order within Apache Airflow, a platform used to programmatically author, schedule, and monitor workflows. Each DAG defines a workflow, which is a series of tasks that need to be executed in a specific order.

 My role is to ensure apache airflow doesn't go down in prod and non prod and also update the docker images and any configuration for its eks instance using kubernetes and helm. 

The second product i am working on is the xena chatbot from the advanced gen ai analytics squad. 

The Xena chatbot is designed to enhance the Data Exchange Platform (DEP) at CBA by enabling self-service onboarding for data sharing use cases using generative AI. DEP is a cloud-based platform that facilitates seamless, secure, and efficient data sharing between CBA and its third-party partners. Traditionally, the DEP team has been involved in setting up data pipelines for new data sharing initiatives. The Xena chatbot aims to automate this process by capturing metadata from business users through natural language interaction, generating tenant-specific infrastructure code, and dynamically creating DEP core libraries based on business metadata. This automation improves code quality, readability, and consistency, reducing manual effort and ensuring high standards of data integrity and compliance. By integrating tools like github actions and Confluence, the Xena chatbot streamlines the entire pipeline generation process, enhancing collaboration, productivity, and regulatory compliance.

My contributions on the xena product i am working on includes:
 
* Parquet file parsing for human readable format on XENA UI and upload showing/hiding. Hiding and showing the upload button is necessary to ensure it only appears when the chatbot detects a specific prompt with enough relevant keywords, each weighted to trigger the button's visibility, thereby enhancing user experience by displaying it contextually.
* Added styling formating
* Implementing a new login page based on UX design.
* Creating RDS instances on AWS, creating a user table and integrating them with the login functionality.
* Implementing logout functionality.
* Integrating the GENAI GitHub service account in the Toolkit trigger which is a pipeline deployment trigger by updating the lambda function code to use a different authentication method and updating the branch naming methodology.

## b) What are the most complex technical components of the product and how have you contributed to overcoming those complexities?

The most complex technical component I worked on was the Kafka pipeline split for the FRAUMD (fraud detection) and CBIRBS (customer behavioural insights - retail banking services) pipelines.

The reason why we are splitting the pipeline is to minimise single points of failure and improves load balancing by distributing the workload across multiple components, reducing the risk of a complete system outage and ensuring more efficient resource utilisation. This hence reduces risk of the system failing and downtime which is crucial for cba as we have a very low fault tolerance.

I used Apache Kafka, which is a tool designed for building real-time data pipelines and streaming applications which is crucial for our team's product.

My work involved creating and configuring these Kafka pipelines, including both the publisher and streamer, within the `adc-fraumd-stg` namespace. I conducted a full end-to-end test to ensure the pipeline's functionality, which included creating Helm charts for the cee-publisher-mar application, configuring relevant secrets in Secrets Manager, and executing a comprehensive test run. This test run involved publishing to the Snowflake test table, Kafka Publisher, Kafka topic STG, Kafka streamer, and Oracle CEE MAR_RT, ensuring seamless data flow and integration.

Then, I had to run a full test run of publishing to the `Snowflake test table` → `Kafka Publisher` → `Kafka topic STG` → `Kafka streamer` → `Oracle CEE MAR_RT`.

* FRAUMD Kafka topic - Test Results
  * This document details test results for the bespoke Kafka pipeline for the FRAUMD domain use-case.
  * https://commbank.atlassian.net/wiki/spaces/CCS/pages/916112283/FRAUMD+Kafka+topic+-+Test+Results

## c) What is your most valued contribution to the product?

The most valued contribution to my product is the GitHub Enterprise Cloud (GHEC) migration. This task was critical as it aligns with Pillar 2 of our crew's objectives: A modern technology estate. By migrating from on-premises to the cloud, we ensure that our technology stack is up-to-date, scalable, and secure. This migration benefits CBA by streamlining our development workflows and enhancing security, ultimately improving our team's efficiency and satisfaction. This helps our team work more smoothly and securely, making our processes faster and more reliable.

 This task involves extensive connectivity configuration, such as configuring the `calico network` to allow egress to the app-proxy, which is necessary for Airflow to sync the DAGs from the repository. Calico is a networking and network security solution for containers, virtual machines, and native host-based workloads, providing high-performance networking and network policy enforcement.

Egress refers to the outbound traffic from a network. We need to add an endpoint to a Calico policy whitelist to allow specific outbound traffic to that endpoint, ensuring secure and controlled access.

We also needed to properly manage AWS secrets, including the GHEC service account credentials, and set up GitHub app authentication for GitHub workflows using Vault secrets. Additionally, updating GitHub Actions was required. I believe my extensive understanding of Git and GitHub enabled me to accomplish this task effectively. For instance, we needed to sync the branches of the old GitHub repository to the newly created GitHub cloud repository. I achieved this by setting two remotes locally, rebasing, fixing a myriad of merge conflicts, and then pushing the branches from the old repository to the new repository.

* PR Evidence for configuring network policies: 
  * https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters/pull/4858
  * https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters/pull/4846

I also made significant contributions to the Apache Airflow tech stack, an open-source tool widely used at CBA. My ability to set up Airflow and contribute to its source code demonstrates my exemplary skills as a developer. This work not only indirectly benefited everyone at CBA who relies on this tool but also every engineer and organisation that are using it as well elsewhere!

My contributions to the official Apache Airflow open-source tool indirectly benefit CBA by enhancing the overall functionality and usability of Airflow, which is widely used within CBA for orchestrating complex workflows and data pipelines. These contributions are:

* PR i created and merged for the official apache airflow open source tool:
  * For apache airflow, I have updated the URL to reflect changes in the `dagDisplayNamePattern`. I also created an enum in searchParams.ts. I am using a debounce logic for it as well
  * https://github.com/apache/airflow/pull/42896

The issue i was assigned to on the official apache airflow open source repo are:
* The public get dags endpoints in FastAPI now supports `dag_display_name_pattern`. We should use that to search DAGs in the UI and activate the disabled search bar that is already there.
  * https://github.com/apache/airflow/issues/42714#issuecomment-2426680190
* Turn the "Admin" button in the Nav into a menu, like we do with Docs or User with a Connections option. Add a Connections page. Within the Connections page, load the list of connections and render them in a table using our DataTable component. This should include limit/offset pagination and allow order_by columns that the API supports.
  * https://github.com/apache/airflow/issues/43703

### Supporting artefacts and information

Consider how you contribute to the Technology Strategy. Provide links to your contributions (ie solving blocker board items, mentoring others, optimising or automating toil, introducing modern technical practices to your squad/s eg shift left testing, contributing to the engineering handbook etc).

* Blogpost i used for mentoring other commsee 2 grads on how to use react and css:
  * https://llcode.tech/digital-chronicles/blog/66e0359b18eb5f86ea13b52d
* How to Run Airflow on Dag Repo Locally
  * This Confluence page provides a step-by-step guide on how to run Apache Airflow DAGs locally on a development laptop using port 8080. It allows engineers to run and test Airflow DAGs locally, which speeds up the development and debugging process.
  * https://commbank.atlassian.net/wiki/spaces/CCS/pages/1028566055/How+to+Run+Airflow+on+Dag+Repo+Locally
* How to Publish a Docker Image to Artifactory?
  * This Confluence page provides a step-by-step guide on creating and publishing a Docker image to Artifactory. This streamlines the process of creating and publishing Docker images, enhancing efficiency and consistency in deploying containerized applications within CBA.
  * https://commbank.atlassian.net/wiki/spaces/CCS/pages/1061128756/How+to+Publish+a+Docker+Image+to+Artifactory
* How to Implement a Retry Policy on the whole DAG when a Task Fails
  * https://commbank.atlassian.net/wiki/spaces/CCS/pages/1029104419/How+to+Implement+a+Retry+Policy+on+the+whole+DAG+when+a+Task+Fails
* Observe Dashboard for Airflow Handbook
  * To teach POs and other engineers on how to use the new observe dashboard after migration from using splunk for cost savings and as part of the devSecOps movement.
  * https://commbank.atlassian.net/wiki/spaces/CCS/pages/1031439681/Observe+Dashboard+for+Airflow+Handbook
* How to Setup AWS Codebuild with Github
  * https://commbank.atlassian.net/wiki/spaces/CCS/pages/1086188070/How+to+Setup+AWS+Codebuild+with+Github
  * This guide provides instructions on setting up a CodeBuild pipeline using the `adc.integration-framework` repository.
  
#### Confluence Pages I have Contributed to for Housekeeping
* https://commbank.atlassian.net/wiki/spaces/CCS/pages/1013088888/Runsheet+Github+Migration+PROD
* https://commbank.atlassian.net/wiki/spaces/CCS/pages/1004508095/Analysis+-+Migration+of+Airflow+to+AWS+Managed+Airflow+Service
* https://commbank.atlassian.net/wiki/spaces/CCS/pages/916112283/FRAUMD+Kafka+topic+-+Test+Results
* https://commbank.atlassian.net/wiki/spaces/CCS/pages/900014497/Splunk+queries+to+Observe
* https://commbank.atlassian.net/wiki/spaces/CCS/pages/705702737/Onboarding+-+MLOPs+Publishing+and+Orchestration+Squad

## How have you contributed to improving engineering at CBA?
I have contributed to improving engineering at CBA by addressing an issue in the Homebrew setup guide on the engineering handbook. When users followed the guide to install Homebrew and encountered an error with the brew install `jq` command, I created a script that bypasses the need to have jq installed. This aides in the speedup of the onboarding process. This solution ensures a smoother setup process for users, even when Artifactory is not set up, thereby enhancing the overall efficiency and reliability of our engineering practices.

* PR Added brew_login script that doesn't require jq. #94
  * https://github.com/CBA-General/docs.engineering-handbook/pull/94

I made significant contributions to the Apache Airflow tech stack, an open-source tool widely used at CBA. My ability to set up Airflow and contribute to its source code demonstrates my exemplary skills as a developer. This work not only indirectly benefited everyone at CBA who relies on this tool but also every engineer and organisation that are using it as well elsewhere!

* PR Add search by `dag_display_name_pattern` on dag list page with rebase for airflow 
  * https://github.com/apache/airflow/pull/42896

I also improved automation and branch naming by integrating the GENAI GitHub service account in the Toolkit trigger (a pipeline deployment trigger) by updating the lambda function code to use a more relaliable authentication method and updating the branch naming methodology. This allows for more efficient triggering of workflows and tasks, reducing manual intervention and increasing overall productivity.

* PR for changing authnetication method for toolkit trigger lambda function to use github app method.
  * PR evidence: https://github.com/CBA-General/dep-GenEx.AI/pull/19

I integrated a code formatting script using `prettier` into the `package.json` and created an `.editorconfig` file for the Xena chatbot frontend. Prettier is an opinionated code formatter available as an npm package. It enforces a consistent style by parsing your code and re-printing it with its own rules, which include handling things like line lengths, indentation, and spacing. So when the developers push code onto the repo it will be formatted in a consistent manner, This initiative significantly enhanced engineering by improving code quality and readability. The integration of Prettier enforces consistent code formatting, thereby reducing syntax errors and manual formatting efforts. The .editorconfig file standardizes development environments across the team, ensuring uniformity in coding practices. These technical enhancements make the codebase easier to read, review, and maintain, ultimately fostering a more efficient and cohesive development workflow.

* parquet file parsing for human readable format on xena UI #20 #25
  * https://github.com/CBA-General/dep-GenEx.AI-ui/pull/25


## Supporting artefacts and information
* PR contribution to engineering handbook:
  * https://github.com/CBA-General/docs.engineering-handbook/pull/94

Provide links as evidence to the body of work, portfolio or other suitable artefacts (ie Github repo's, design documents etc).

## a) Describe examples where you mentored other engineers

I created a presentation as well as a created new handbook on confluence on how to use the observe dashboard for airflow. These engineers include senior engineers and product owners. This provides clear, accessible guidance for engineers, including senior engineers and product owners, on how to effectively use the Observe Dashboard for Airflow. It ensures that team members can quickly understand and utilise the dashboard, leading to more efficient monitoring and management of workflows.

Evidence: https://commbank.atlassian.net/wiki/spaces/CCS/pages/1031439681/Observe+Dashboard+for+Airflow+Handbook

I presented in front other engineers on the team how to utilise apache airflow which is a toool we are using for workflow management and it can perform dynamic workflow creation and scheduling and monitoring tasks. By demonstrating how to use Apache Airflow for workflow management, I help other engineers understand its capabilities for dynamic workflow creation, scheduling, and monitoring. This knowledge transfer enhances the team's ability to manage complex workflows effectively, leading to improved productivity and workflow optimisation.

I create a retry policy template for apache airflow and i created a workshop to teach other engineers on how I implemented it. The retry policy template ensures that tasks within Airflow are retried appropriately upon failure, enhancing the reliability and robustness of workflows. The workshop educates enginee
Evidence: https://commbank.atlassian.net/wiki/spaces/CCS/pages/1029104419/How+to+Implement+a+Retry+Policy+on+the+whole+DAG+when+a+Task+Fails

I also demonstrate a great deal of initiative when it comes to sharing my knowledge with other engineers. Since I possess a great deal of frontend software engineering knowledge, I took the initiative to organise a bootcamp for the entire CommSee team's grads on how to use React and CSS. This bootcamp equips new graduates with essential frontend development skills, specifically in React and CSS, fostering a more skilled and capable team. It promotes knowledge sharing and accelerates the onboarding process, enabling graduates to contribute more effectively to projects.
 
Blog post evidence: https://llcode.tech/digital-chronicles/blog/66e0359b18eb5f86ea13b52d

I also showcase strong coding capabilities within my team, which leads my teammates to frequently seek my assistance, particularly with matters related to Apache Airflow and EKS clusters/Kubernetes. Additionally, I respond swiftly to messages and requests, such as when engineers ask for write permissions to repositories. My expertise in Apache Airflow and EKS clusters/Kubernetes, along with my prompt response to requests, ensures that my teammates can rely on me for technical support. This leads to quicker resolution of issues, smoother project progress, and a collaborative team environment where knowledge is freely shared.
 
Photo evidence:

## b) What improvements did you observe in the people you mentored?

* After the React bootcamp, the CommSee grads reported having more knowledge on frontend development, which they have started applying to their projects, leading to improved UI/UX and more efficient development practices.

* After my presentation on the new Observe Dashboard in front of the POs and senior engineers, my team reported increased interest in adopting the Observe Dashboard and expressed satisfaction with the utility of the dashboard I created. They expressed interest in me hosting more workshops for their separate squads on how to do this.

## ) What is the most effective method of mentoring you have experienced?

My Technical Manager offers coaching through regular catch-ups, approximately every fortnight. His positive attitude and encouragement keep me motivated and make me feel confident about my work. During our catch-ups, he often inquires if I have any questions or needs from the team, showing the team's dedication to keeping me informed and valuing my input. This helps me understand the team better and provides an opportunity to voice any concerns, although I haven't had any since the system has been working exceptionally well.

During my rotation, I was assigned a technical buddy who I can turn to for understanding key concepts and knowing which permissions to request. He also assigns me tasks and is responsible for onboarding me by referring me to Confluence pages and documentation. For example, he helped me understand the solution architecture of the fraud and CBIRBS pipeline by showing me a diagram. This has helped me grasp the ins and outs of the team. He is doing an excellent job because I feel increasingly independent within the team and able to work alongside him, helping to ease the team's workload.
 

My tech buddy also provided invaluable mentoring by holding presentations explaining the business and product aspects, and how everything we build connects to the Next Best Conversations and Customer Engagement Engine. This broader perspective helped me see the value in our team's work and understand how my contributions improve the bank overall. Grasping the context of my work is essential for me to excel in my role.

Despite all this support, I have consistently demonstrated autonomy throughout my rotation, finding that solving problems on my own is highly effective for understanding and learning about my team's work. The overwhelming support I receive from my team complements my autonomy perfectly, creating an ideal balance. I feel equipped with all the tools and resources I need to succeed.

### Supporting artefacts and information

Provide links (ie PR's) you are proud of, showing quality code review, github stats on commits, recognitions for our values as they relate to engineering etc.

#### Repository i have contributed to:
* https://github.com/CBA-General/dep-genex.ai-ui
* https://github.com/CBA-General/dep-genex.ai
* https://github.com/CBA-General/adc.airflow.dag
* https://github.com/CBA-General/adc.airflow.config
* https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps
* https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters
* https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework
* https://github.com/CBA-CommBank/MyProperty

#### My PR Requests

* Add docker-artifactory token secret retrieval.
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/581

* Feature/sprvrs 1986 incl status categories for airflow
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps

* Added cee-publisher-mar to prod environment:
  * https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/560
  * This PR updates the Kafka endpoints and implements a new architecture for the Kafka pipeline to enhance the scalability and reliability of the model score output stream to CEE. The current Kafka pipeline configuration faces several challenges:
    * Capacity Bottlenecks: The common Kafka topic may hit capacity limits (currently 20GB) as more models are added, leading to potential message loss.
    * Single Point of Failure: Issues in the common streamer instance can impact the output to CEE for all models.
    * Scalability Limitations: The current setup cannot scale effectively due to storage and processing limitations, leading to performance slowdowns as more models are added. To address these issues, we propose a new architecture that provisions use case-specific publishers, Kafka topics, and streamer instances. This approach will enhance scalability, reduce the risk of message loss, and isolate the impact of any issues to specific use cases.

* Added cee-publisher-mar to prod environment. #515
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/515

* Feature/sprvrs 1572 fraumd kafka topic staging implementation #517
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/517

* Fix customer oracle url address causing connection issue. #523
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/523

* Updated airflow values to include ghec and airflow-git-sync-secrets. #526
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/526

* Added secrets for adc-fraumd-stg stg-kafka-publisher-cvs #527
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/527

* Updated airflow values to include ghec and airflow-git-sync-secrets
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/528

* Update image version.
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/529

* Fix bootstrap servers they were publishing to nft
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/530

* Add rule that allows Ingress from specific IP ranges for Airflow #4846
https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters/pull/4846

* SPRVRS-1482 Add rule that allows Ingress from specific IP ranges for … #4858
https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters/pull/4858

* Add docker-artifactory token secret retrieval.
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/581

* Updated the Kafka endpoints based on the links provided at the end of the Confluence page
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/560

* PR for custom docker image:
https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework/pull/67

* PR i created and merged for the official apache airflow open source tool:
https://github.com/apache/airflow/pull/42896

* The issue i was assigned to on the official apache airflow open source repo are:
https://github.com/apache/airflow/issues/42714#issuecomment-2426680190
https://github.com/apache/airflow/issues/43703

* PR contribution to engineering handbook:
https://github.com/CBA-General/docs.engineering-handbook/pull/94

* PR contribution to Apache Airflow repo (the tool we are using at cba):
https://github.com/apache/airflow/pull/42896

* PR for Added file for performing cee reconciliation alert testing.
https://github.com/CBA-General/adc.airflow.dag/pull/112

* PR for parquet file parsing for human readable format on xena UI:
https://github.com/CBA-General/dep-GenEx.AI-ui/pull/25

* Updated toolkit trigger authentication method and lamda function for parsing parquet file (1 PR for two separate tickets)
https://github.com/CBA-General/dep-GenEx.AI/pull/19

* PR Update prod configs to use ghec. #548
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/548

* Feature/sprvrs 2009 build custom airflow docker image #67
https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework/pull/67

* Added mwaa cloudformation template. #481
https://github.source.internal.cba/PublicCloudLandingZoneExceptions/cba-a-ani-cdao_hosting-custom/pull/481

* Feature/sprvrs 2009 build custom airflow docker image #67
https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework/pull/67

#### PR I have reviewed
* https://github.source.internal.cba/AnalyticsInformation/adc.airflow.config/pull/410
* https://github.com/CBA-General/adc.airflow.dag/pull/24
* https://github.com/CBA-General/adc.airflow.dag/pull/37
* https://github.source.internal.cba/AnalyticsInformation/adc.airflow.dag/pull/1404

#### Other PRs from my last rotation
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/665
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/662
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/660
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/652
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/643
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/631
* https://github.source.internal.cba/DigitalChannels/Azure.EnvironmentDefinition/pull/20778
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/621
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/620
* https://github.source.internal.cba/DigitalChannels/Azure.EnvironmentDefinition/pull/20666
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/618
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/615
* https://github.source.internal.cba/DigitalChannels/ManageMyHomeLoan/pull/4
* https://github.source.internal.cba/DigitalChannels/ManageMyHomeLoan/pull/3
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/599
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/598
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/592
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/589
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/581
* https://github.source.internal.cba/DigitalChannels/myproperty/pull/586

## What are your most valuable engineering qualities?

My most valuable engineering qualities include my diverse skill set, which has been consistently demonstrated across various workplaces. For instance, during my last rotation, I was able to immediately tackle and complete all my assigned tickets. Similarly, in my current team, I quickly dove into challenging tickets right from the start. In my first week of the initial rotation, I completed five development tickets, and at the beginning of my second rotation, I successfully handled two more.
 
I have received consistent feedback from various teammates and technical managers throughout my two rotations, highlighting my autonomy, quick learning ability, and efficient problem-solving skills. I possess extensive experience in both frontend and backend development, as well as in machine learning and DevOps. For example, I have demonstrated proficiency in technologies such as Apache Kafka, Airflow, Docker, Kubernetes, and frontend frameworks like React. In my current team, I configured the FRAUMD Kafka publisher and streamer pipeline in the adc-fraumd-stg namespace and worked on the Xena chatbot frontend, including the Parquet file upload and adding Prettier for the frontend.

My ability to quickly adapt and apply my knowledge has enabled me to complete tasks efficiently. In my last and current rotations, both of which involved frontend work, I was able to finish tickets rapidly due to my React expertise. This versatility and agility allow me to excel in any software engineering team, contributing effectively to project success.

My technical manager has praised my capability and autonomy, noting that I finish work very quickly and has no negative feedback for me.

Based on the feedbacks, my team observed that I collaborated very well and efficiently, always willing to help and share knowledge within the graduate cohorts. They noted my diligence, intelligence, strong technical skills, and growth mindset, which suggest that I always strive to deliver the best solutions and high-quality results to our customers.

My team also appreciated my ability to pick up tickets straight away, tackle fears, and step outside my comfort zone. They highlighted my great support in looking into issues or approving PRs late in the afternoon.
 
### Supporting artefacts and information

Provide links or other artefacts on your plans to upskill or raise the bar (ie development plan).

## What skills and behaviours can you enhance to support your career progression?
I believe continuous learning is key to facilitating my career progression. I plan to dedicate time both at work and on my own to watch and read engineering materials and videos, as well as engage in hands-on exploration of new coding methods and technologies. My current team utilizes a variety of cutting-edge tech stacks, including Apache Kafka, Apache Airflow, Python, Docker, Java, .NET, Flask, Kubernetes, Amazon EKS, Amazon Secrets Management, other AWS technologies, and even React!

I can illustrate my commitment to continuous learning. I can recognise the need to stay updated with the latest technologies to advance my career, to improve my skills and knowledge, I decided to pursue additional learning opportunities outside of my regular work hours. I completed numerous Codecademy certifications and worked on my own projects in my spare time. Additionally, I have GitHub contributions to my side hustles and projects outside of work. Result: These efforts have made me an avid learner, continuously improving my technical capabilities and staying current with industry trends.

I firmly believe that honing my communication skills will enhance my career progression. My current team provides numerous opportunities for me to demo the things I have built, which are topics I am very confident about. This serves as excellent practice for improving my communication abilities.

Photo evidence of workshop meetings I am running:


### Supporting artefacts and information
* https://www.codecademy.com/profiles/luyangliuable/certificates/ffd0f42cce1a44e9a0108b365047a0a6
* https://www.credly.com/badges/511669ed-91e4-453b-a517-88c67fd3fb9e/public_url
* https://www.codecademy.com/profiles/luyangliuable/certificates/5cab64c55f1de8039db366ef
* https://www.codecademy.com/profiles/luyangliuable/certificates/8c3029c4a6e5894e74da756e3a7c0ae3
* https://www.codecademy.com/profiles/luyangliuable/certificates/56fb1e71303e37b643bb1905f31c8a09
* https://www.codecademy.com/profiles/luyangliuable/certificates/042a4e5884e3eb6ea1f2a12be6abb851
* https://www.codecademy.com/profiles/luyangliuable/certificates/9da8e26980d5139405439ee7578b8b69
* https://www.codecademy.com/profiles/luyangliuable/certificates/c87ba0541f8be78bc2f4ba1128233f6f
* https://www.codecademy.com/profiles/luyangliuable/certificates/37c55263a9f1b1f7603f7551c293ecbd
