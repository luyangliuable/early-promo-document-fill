https://commbank.sharepoint.com/sites/onecba-engineering/SitePages/Applicants.aspx

Provide links as evidence to the body of work, portfolio or other suitable artefacts (ie Github repo's, design documents etc).

Github repo:
https://github.source.internal.cba/liul31 (227 contributions in the last year)
https://github.com/Lucas-Liu_cba (287 contributions)

Website
https://LLcode.tech

a) What product/s do you work on and what is your role in that product's development?
I am currently doing work across two different squads.

One of the product I am involved with is the publishing and orchestration framework. This framework is crucial for managing the execution, transformation, and loading of model outputs. My role involves developing and maintaining this framework to ensure it meets the functional requirements as outlined in our user stories. Specifically, I focus on automating model job executions, transforming model outputs, and ensuring data quality through various validation checks.

The second product i am working on is the xena chatbot from the advanced gen ai analytics squad. This My role in this product includes:
* Parquet file parsing for human readable format on XENA UI and upload showing/hiding.
* Added styling formating
* Implementing a new login page based on UX design.
* Creating RDS instances on AWS and integrating them with the login functionality.
* Implementing logout functionality.
* Integrating the GENAI GitHub service account in the Toolkit trigger by updating the lambda function code to use a different authentication method and updating the branch naming methodology.

b) What are the most complex technical components of the product and how have you contributed to overcoming those complexities?

The most complex technical component I worked on was the Kafka pipeline split for the FRAUMD and CBIRBS pipelines. This involved creating and configuring the Kafka pipeline, including both the publisher and streamer, within the adc-fraumd-stg namespace. I conducted a full end-to-end test to ensure the pipeline's functionality, which included creating Helm charts for the `cee-publisher-mar` application, configuring relevant secrets in Secrets Manager, and executing a comprehensive test run. This test run involved publishing to the Snowflake S07 test table, Kafka Publisher, Kafka topic STG, Kafka streamer, and Oracle CEE MAR_RT, ensuring seamless data flow and integration.

Then I had to run a full test run of publishing to Snowflake S07 test table → Kafka Publisher → Kafka topic STG → Kafka streamer → Oracle CEE MAR_RT

c) What is your most valued contribution to the product?


Supporting artefacts and information

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

* How have you contributed to improving engineering at CBA?
* Supporting artefacts and information

Provide links as evidence to the body of work, portfolio or other suitable artefacts (ie Github repo's, design documents etc).
a) Describe examples where you mentored other engineers
I have connections with the grads from the commsee team.

I created a presention for how to create the observe dashboard.

I walked through in front of other engineers on the team how to _

I create a retry policy template for apache airflow and i created a meeting in front of other engineers on how I implemented it

b) What improvements did you observe in the people you mentored?


c) What is the most effective method of mentoring you have experienced?
Regular meetings with my TM and also a technical buddy when i can turn to to understand key concepts and know what permissions i need to request. I have consistent demonstrated autonomy throughout the rotation.

Supporting artefacts and information

Provide links (ie PR's) you are proud of, showing quality code review, github stats on commits, recognitions for our values as they relate to engineering etc.

Add docker-artifactory token secret retrieval.
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/581

Feature/sprvrs 1986 incl status categories for airflow
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps

## Added cee-publisher-mar to prod environment:
https://github.source.internal.cba/DataExchangeProducts/apihosting-eks-apps/pull/560

### What
This PR updates the Kafka endpoints and implements a new architecture for the Kafka pipeline to enhance the scalability and reliability of the model score output stream to CEE.

### Why
The current Kafka pipeline configuration faces several challenges:
Capacity Bottlenecks: The common Kafka topic may hit capacity limits (currently 20GB) as more models are added, leading to potential message loss.
Single Point of Failure: Issues in the common streamer instance can impact the output to CEE for all models.
Scalability Limitations: The current setup cannot scale effectively due to storage and processing limitations, leading to performance slowdowns as more models are added.
To address these issues, we propose a new architecture that provisions use case-specific publishers, Kafka topics, and streamer instances. This approach will enhance scalability, reduce the risk of message loss, and isolate the impact of any issues to specific use cases.

### How
Update Kafka Endpoints:

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


*
What are your most valuable engineering qualities?
*
Supporting artefacts and information

Provide links or other artefacts on your plans to upskill or raise the bar (ie development plan).
* What skills and behaviours can you enhance to support your career progression?
* Supporting artefacts and information
