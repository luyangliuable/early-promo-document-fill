https://commbank.sharepoint.com/sites/onecba-engineering/SitePages/Applicants.aspx

## Provide links as evidence to the body of work, portfolio or other suitable artefacts (ie Github repo's, design documents etc).

### Github repo:
https://github.source.internal.cba/liul31 (227 contributions in the last year)
https://github.com/Lucas-Liu_cba (287 contributions)

### Website
https://LLcode.tech

## a) What product/s do you work on and what is your role in that product's development?
I am currently doing work across two different squads.

One of the product I am involved with is the publishing and orchestration framework. This framework is crucial for managing the execution, transformation, and loading of model outputs. My role involves developing and maintaining this framework to ensure it meets the functional requirements as outlined in our user stories. Specifically, I focus on automating model job executions, transforming model outputs, and ensuring data quality through various validation checks. My key contributions are:

* Performed airflow strategic alert uplift image testing, by ensuring All existing flows are validated with new docker image.
* Built and pushed a custom Airflow Docker image with the updated Amazon provider package to Artifactory, then test it in the non-production environment to ensure all existing DAGs remain functional and resolve the GlueSensorOperator error.
* Created and configure the FRAUMD Kafka publisher and streamer pipeline in the adc-fraumd-stg namespace, then perform a full end-to-end test, including Helm charts creation, secrets management, and a complete test run from Snowflake to Oracle CEE.
 
As part of maintaining and building the publishing and orchestration framework, we also utilised a tool called apache airflow which is a workflow management application that can perform dynamic workflow creation and scheduling and monitoring tasks. My role is to ensure apache airflow doesn't go down in prod and non prod and also update the docker images and any configuration for its eks instance using kubernetes and helm. 

The second product i am working on is the xena chatbot from the advanced gen ai analytics squad. 

The Xena chatbot is designed to enhance the Data Exchange Platform (DEP) at CBA by enabling self-service onboarding for data sharing use cases using generative AI. DEP is a cloud-based platform that facilitates seamless, secure, and efficient data sharing between CBA and its third-party partners. Traditionally, the DEP team has been involved in setting up data pipelines for new data sharing initiatives. The Xena chatbot aims to automate this process by capturing metadata from business users through natural language interaction, generating tenant-specific infrastructure code, and dynamically creating DEP core libraries based on business metadata. This automation improves code quality, readability, and consistency, reducing manual effort and ensuring high standards of data integrity and compliance. By integrating tools like GitHub and Confluence, the Xena chatbot streamlines the entire pipeline generation process, enhancing collaboration, productivity, and regulatory compliance.

My contributions on the xena product i am working on includes:
 
* Parquet file parsing for human readable format on XENA UI and upload showing/hiding.
* Added styling formating
* Implementing a new login page based on UX design.
* Creating RDS instances on AWS, creating a user table and integrating them with the login functionality.
* Implementing logout functionality.
* Integrating the GENAI GitHub service account in the Toolkit trigger by updating the lambda function code to use a different authentication method and updating the branch naming methodology.

## b) What are the most complex technical components of the product and how have you contributed to overcoming those complexities?

The most complex technical component I worked on was the Kafka pipeline split for the FRAUMD (fraud detection) and CBIRBS (customer behavioural insights - retail banking services) pipelines. This involved creating and configuring the Kafka pipeline, including both the publisher and streamer, within the adc-fraumd-stg namespace. I conducted a full end-to-end test to ensure the pipeline's functionality, which included creating Helm charts for the cee-publisher-mar application, configuring relevant secrets in Secrets Manager, and executing a comprehensive test run. This test run involved publishing to the Snowflake S07 test table, Kafka Publisher, Kafka topic STG, Kafka streamer, and Oracle CEE MAR_RT, ensuring seamless data flow and integration.

Then, I had to run a full test run of publishing to the Snowflake S07 test table → Kafka Publisher → Kafka topic STG → Kafka streamer → Oracle CEE MAR_RT.

## c) What is your most valued contribution to the product?

The most valued contribution to my product is the GitHub Enterprise Cloud (GHEC) migration. This task involves extensive connectivity configuration, such as configuring the `calico network` to allow egress to the app-proxy, which is necessary for Airflow to sync the DAGs from the repository. We also needed to properly manage AWS secrets, including the GHEC service account credentials, and set up GitHub app authentication for GitHub workflows using Vault secrets. Additionally, updating GitHub Actions was required. I believe my extensive understanding of Git and GitHub enabled me to accomplish this task effectively. For instance, we needed to sync the branches of the old GitHub repository to the newly created GitHub cloud repository. I achieved this by setting two remotes locally, rebasing, and then pushing the branches from the old repository to the new repository.

### Supporting artefacts and information

Consider how you contribute to the Technology Strategy. Provide links to your contributions (ie solving blocker board items, mentoring others, optimising or automating toil, introducing modern technical practices to your squad/s eg shift left testing, contributing to the engineering handbook etc).

Blogpost i used for mentoring:
https://llcode.tech/digital-chronicles/blog/66e0359b18eb5f86ea13b52d

https://commbank.atlassian.net/wiki/spaces/CCS/pages/1028566055/How+to+Run+Airflow+on+Dag+Repo+Locally
https://commbank.atlassian.net/wiki/spaces/CCS/pages/1061128756/How+to+Publish+a+Docker+Image+to+Artifactory
https://commbank.atlassian.net/wiki/spaces/CCS/pages/1029104419/How+to+Implement+a+Retry+Policy+on+the+whole+DAG+when+a+Task+Fails
https://commbank.atlassian.net/wiki/spaces/CCS/pages/1031439681/Observe+Dashboard+for+Airflow+Handbook
https://commbank.atlassian.net/wiki/spaces/CCS/pages/1013088888/Runsheet+Github+Migration+PROD
https://commbank.atlassian.net/wiki/spaces/CCS/pages/1004508095/Analysis+-+Migration+of+Airflow+to+AWS+Managed+Airflow+Service

https://commbank.atlassian.net/wiki/spaces/CCS/pages/916112283/FRAUMD+Kafka+topic+-+Test+Results
https://commbank.atlassian.net/wiki/spaces/CCS/pages/900014497/Splunk+queries+to+Observe
https://commbank.atlassian.net/wiki/spaces/CCS/pages/705702737/Onboarding+-+MLOPs+Publishing+and+Orchestration+Squad

## How have you contributed to improving engineering at CBA?
I have contributed to improving engineering at CBA by addressing an issue in the Homebrew setup guide on the engineering handbook. When users followed the guide to install Homebrew and encountered an error with the brew install jq command, I created a script that bypasses the need to have jq installed. This solution ensures a smoother setup process for users, even when Artifactory is not set up, thereby enhancing the overall efficiency and reliability of our engineering practices.

I also improved automation and branch naming by integrating the GENAI GitHub service account in the Toolkit trigger by updating the lambda function code to use a different authentication method and updating the branch naming methodology. This allows for more efficient triggering of workflows and tasks, reducing manual intervention and increasing overall productivity.

I integrated a code formatting script using `Prettier` into the `package.json` and created an `.editorconfig` file for the Xena chatbot frontend. So when dev push code onto the repo it will be formatted in a consistent manner, This initiative significantly enhanced engineering by improving code quality and readability. The integration of Prettier enforces consistent code formatting, thereby reducing syntax errors and manual formatting efforts. The .editorconfig file standardizes development environments across the team, ensuring uniformity in coding practices. These technical enhancements make the codebase easier to read, review, and maintain, ultimately fostering a more efficient and cohesive development workflow.

## Supporting artefacts and information
PR contribution to engineering handbook:
https://github.com/CBA-General/docs.engineering-handbook/pull/94

Provide links as evidence to the body of work, portfolio or other suitable artefacts (ie Github repo's, design documents etc).

## a) Describe examples where you mentored other engineers

I have connections with the grads from the commsee team, and since I possess a great deal of frontend software engineering knowledge I organised a bootcamp for the entire commsee team's grads on how to use react and css.

I created a presentation as well as a created new handbook on confluence on how to use the observe dashboard for airflow. These engineers include senior engineers and product owners.

I presented in front other engineers on the team how to utilise apache airflow.

I create a retry policy template for apache airflow and i created a workshop to teach other engineers on how I implemented it.

## b) What improvements did you observe in the people you mentored?

* After the react bootcamp the commsee grads reported having more knowledge on the frontend.
* After my presention on the new observe dashboard in front of the POs and senior engineers, my team reported interest in also adopting the observe dashboard and they are happy to utilise the dashboard i created.

## ) What is the most effective method of mentoring you have experienced?

TM coaches me by providing me with regularly catchups (roughly fortnightly) and on the rotation i was assigned a technical buddy who i can resort to for understanding key concepts and know what permissions i need to request. My TM is very positive and provides a lot of encouragements which makes me really motivated to do work and feel positive about the things i do.

I have consistently demonstrated autonomy throughout my rotation, so i find solving problems on my own also really effective in understanding and learning about the work on my team. I feel like i am equiped with all the tools and resources I need to be able 

Supporting artefacts and information

Provide links (ie PR's) you are proud of, showing quality code review, github stats on commits, recognitions for our values as they relate to engineering etc.

## Repository i have contributed to:
https://github.com/CBA-General/dep-genex.ai-ui
https://github.com/CBA-General/dep-genex.ai
https://github.com/CBA-General/adc.airflow.dag
https://github.com/CBA-General/adc.airflow.config
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps
https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters
https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework
https://github.com/CBA-CommBank/MyProperty

Add docker-artifactory token secret retrieval.
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/581

Feature/sprvrs 1986 incl status categories for airflow
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps

## Added cee-publisher-mar to prod environment:
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/560

This PR updates the Kafka endpoints and implements a new architecture for the Kafka pipeline to enhance the scalability and reliability of the model score output stream to CEE. The current Kafka pipeline configuration faces several challenges:
Capacity Bottlenecks: The common Kafka topic may hit capacity limits (currently 20GB) as more models are added, leading to potential message loss.
Single Point of Failure: Issues in the common streamer instance can impact the output to CEE for all models.
Scalability Limitations: The current setup cannot scale effectively due to storage and processing limitations, leading to performance slowdowns as more models are added. To address these issues, we propose a new architecture that provisions use case-specific publishers, Kafka topics, and streamer instances. This approach will enhance scalability, reduce the risk of message loss, and isolate the impact of any issues to specific use cases.

Added cee-publisher-mar to prod environment. #515
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/515

Feature/sprvrs 1572 fraumd kafka topic staging implementation #517
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/517

Fix customer oracle url address causing connection issue. #523
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/523

Updated airflow values to include ghec and airflow-git-sync-secrets. #526
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/526

Added secrets for adc-fraumd-stg stg-kafka-publisher-cvs #527
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/527

Updated airflow values to include ghec and airflow-git-sync-secrets
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/528

Update image version.
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/529

Fix bootstrap servers they were publishing to nft
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/530

Add rule that allows Ingress from specific IP ranges for Airflow #4846
https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters/pull/4846

SPRVRS-1482 Add rule that allows Ingress from specific IP ranges for … #4858
https://github.source.internal.cba/ApplicationInfrastructure/aws.eks.clusters/pull/4858

Add docker-artifactory token secret retrieval.
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/581

Updated the Kafka endpoints based on the links provided at the end of the Confluence page
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/560

PR for custom docker image:
https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework/pull/67

PR contribution to engineering handbook:
https://github.com/CBA-General/docs.engineering-handbook/pull/94

PR contribution to Apache Airflow repo (the tool we are using at cba):
https://github.com/apache/airflow/pull/42896

PR for Added file for performing cee reconciliation alert testing.
https://github.com/CBA-General/adc.airflow.dag/pull/112

PR forparquet file parsing for human readable format on xena UI:
https://github.com/CBA-General/dep-GenEx.AI-ui/pull/25

PR Update prod configs to use ghec. #548
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/548

Feature/sprvrs 2009 build custom airflow docker image #67
https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework/pull/67

Added mwaa cloudformation template. #481
https://github.source.internal.cba/PublicCloudLandingZoneExceptions/cba-a-ani-cdao_hosting-custom/pull/481

Feature/sprvrs 2009 build custom airflow docker image #67
https://github.source.internal.cba/AnalyticsInformation/adc.integration-framework/pull/67

### PR I have reviewed
https://github.source.internal.cba/AnalyticsInformation/adc.airflow.config/pull/410
https://github.com/CBA-General/adc.airflow.dag/pull/24
https://github.com/CBA-General/adc.airflow.dag/pull/37
https://github.source.internal.cba/AnalyticsInformation/adc.airflow.dag/pull/1404

### PR from last last rotation
https://github.source.internal.cba/DigitalChannels/myproperty/pull/665
https://github.source.internal.cba/DigitalChannels/myproperty/pull/662
https://github.source.internal.cba/DigitalChannels/myproperty/pull/660
https://github.source.internal.cba/DigitalChannels/myproperty/pull/652
https://github.source.internal.cba/DigitalChannels/myproperty/pull/643
https://github.source.internal.cba/DigitalChannels/myproperty/pull/631
https://github.source.internal.cba/DigitalChannels/Azure.EnvironmentDefinition/pull/20778
https://github.source.internal.cba/DigitalChannels/myproperty/pull/621
https://github.source.internal.cba/DigitalChannels/myproperty/pull/620
https://github.source.internal.cba/DigitalChannels/Azure.EnvironmentDefinition/pull/20666
https://github.source.internal.cba/DigitalChannels/myproperty/pull/618
https://github.source.internal.cba/DigitalChannels/myproperty/pull/615
https://github.source.internal.cba/DigitalChannels/ManageMyHomeLoan/pull/4
https://github.source.internal.cba/DigitalChannels/ManageMyHomeLoan/pull/3
https://github.source.internal.cba/DigitalChannels/myproperty/pull/599
https://github.source.internal.cba/DigitalChannels/myproperty/pull/598
https://github.source.internal.cba/DigitalChannels/myproperty/pull/592
https://github.source.internal.cba/DigitalChannels/myproperty/pull/589
https://github.source.internal.cba/DigitalChannels/myproperty/pull/581
https://github.source.internal.cba/DigitalChannels/myproperty/pull/586

## What are your most valuable engineering qualities?

My most valuable engineering qualities include my diverse skill set, autonomous, quick learning ability, and efficient problem-solving skills. I have extensive experience in both frontend and backend development, as well as machine learning and DevOps. For instance, I have demonstrated proficiency in technologies such as Apache Kafka, Airflow, Docker, Kubernetes, and frontend frameworks like React on my current team and configuring the FRAUMD Kafka publisher and streamer pipeline in the adc-fraumd-stg namespace and worked on the xena chatbot frontend which is the parquet file upload and adding prettier for the frontend.

My ability to quickly adapt and apply my knowledge has enabled me to complete tasks efficiently. In my last and current rotations, both of which involved frontend work, I was able to finish tickets rapidly due to my React expertise. This versatility and agility allow me to excel in any software engineering team, contributing effectively to project success.

My technical manager has praised my capability and autonomy, noting that I finish work very quickly and has no negative feedback for me.

Based on the feedbacks, my team observed that I collaborated very well and efficiently, always willing to help and share knowledge within the graduate cohorts. They noted my diligence, intelligence, strong technical skills, and growth mindset, which suggest that I always strive to deliver the best solutions and high-quality results to our customers.

My team also appreciated my ability to pick up tickets straight away, tackle fears, and step outside my comfort zone. They highlighted my great support in looking into issues or approving PRs late in the afternoon.
 
### Supporting artefacts and information

Provide links or other artefacts on your plans to upskill or raise the bar (ie development plan).

## What skills and behaviours can you enhance to support your career progression?
I believe continuous learning can faciliate my career progression and I will try to learn my in my own time as well as at work by watching and reading engineering materials and videos and doing a lot of hands on exploration in new coding methods and technologies.

### Supporting artefacts and information
https://www.codecademy.com/profiles/luyangliuable/certificates/ffd0f42cce1a44e9a0108b365047a0a6
https://www.credly.com/badges/511669ed-91e4-453b-a517-88c67fd3fb9e/public_url
https://www.codecademy.com/profiles/luyangliuable/certificates/5cab64c55f1de8039db366ef
https://www.codecademy.com/profiles/luyangliuable/certificates/8c3029c4a6e5894e74da756e3a7c0ae3
https://www.codecademy.com/profiles/luyangliuable/certificates/56fb1e71303e37b643bb1905f31c8a09
https://www.codecademy.com/profiles/luyangliuable/certificates/042a4e5884e3eb6ea1f2a12be6abb851
https://www.codecademy.com/profiles/luyangliuable/certificates/9da8e26980d5139405439ee7578b8b69
https://www.codecademy.com/profiles/luyangliuable/certificates/c87ba0541f8be78bc2f4ba1128233f6f
https://www.codecademy.com/profiles/luyangliuable/certificates/37c55263a9f1b1f7603f7551c293ecbd
