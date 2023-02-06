
# Google Summer of Code (GSoC) 2023

The SPCL group will apply as an organization to the Google Summer of Code (GSoC) program
for our open-source projects in data-centric programming and serverless computing.
You can find here student project proposals, advice on applying, and introductions to
each project to start using our software.

## Student Proposals

Students interested in a project should get in touch with proposed mentors and discuss
the project ideas. We will provide a proposal template before the applications open.
All students are expected to conduct initial research into the topic, evaluate requirements,
and discuss potential solutions with mentors.
Active collaboration before the application is vital to a successful project proposal.

Students are expected to demonstrate the required level of programming skills.
Projects define their respective entry tasks that should be accomplished before the deadline of the application period.

## Project Ideas

### Serverless

At SPCL, we develop several open-source projects that target Function-as-a-Service (FaaS),
a new cloud paradigm concerned with writing stateless and _serverless_ functions.
our benchmarking suite [SeBS](https://github.com/spcl/serverless-benchmarks),
a serverless ZooKeeper implementation [FaaSKeeper](https://github.com/spcl/faaskeeper),
high-performance and RDMA-based serverless platform [rFaaS](https://github.com/spcl/rFaaS),
a serverless collectives library [FMI](https://github.com/spcl/FMI) for parallel and distributed applications,
and [Process-as-a-Service (PraaS)](https://github.com/spcl/praas), an enhanced serverless model that uses _processes_ instead of functions.

* [[SeBS] Support for new serverless platforms](#sebs-new-serverless-platforms)
* [[SeBS] Adding new serverless benchmarks](#sebs-new-serverless-benchmarks)
* [[SeBS] Support for new performance experiments](#sebs-new-performance-experiments)
* [[SeBS] Adding serverless applications as benchmarks](#sebs-benchmarking-serverless-applications)
* [[rFaaS] Libfabric for fast function invocations](#rfaas-libfabric-for-fast-function-invocations)
* [[FaaSKeeper] Using serverless ZooKeeper in Apache projects](#faaskeeper-using-serverless-zookeeper-in-apache-projects)
* [[FaaSKeeper] Multi-cloud serverless ZooKeeper](#faaskeeper-multi-cloud-serverless-zookeeper)
* [[FMI] Optimized and multi-cloud serverless collectives](#fmi-optimized-and-multi-cloud-serverless-collectives)

#### [SeBS] New serverless platforms
* **Description**: SeBS supports automatic benchmarking of serverless functions on AWS Lambda, Azure Functions, Google Cloud Functions, and OpenWhisk. We would like to expand SeBS with support for new platforms, such as Fission, Knative, Cloudflare Workers, etc. The new functionality would integrate the platform-specific interface into SeBS, allowing our experiments to automatically deploy and invoke functions.
* **Expected outcome**: Adding to SeBS interface to automatically deploy and execute functions on new serverless platforms.
* **Skills required**: Python, Docker. Experience with Kubernetes would be helpful.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number of platforms).
* **Difficulty** - Easy.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [SeBS] New serverless benchmarks
* **Description**: In SeBS, we provide a representative set of functions and we have an ongoing work towards serverless workflows. The serverless field is constantly changing, and new workloads are constantly being implemented. We would like to extend our benchmarking suite with new function candidates, such as utility functions (PDF generation, antivirus scanning) or scientific benchmarks; new invocation types (functions invoked on changes in object storage); and new workflows.
* **Expected outcome**: Contributing to SeBS new benchmarking functions, triggers, and workloads that succesfully execute on already supported platforms.
* **Skills required**: Python, Docker. Basic experience with cloud is expected (functions, object storage, databases). Experience with Node.js and Go might be helpful for some of the benchmarks.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number of benchmarks).
* **Difficulty** - Easy/Medium.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [SeBS] New performance experiments
* **Description**: SeBS includes automatic experiments that evaluate specific performance features of serverless platforms, such as latency and cost of function invocations or invocation overheads. The goal of the project would be to add new experiments that use microbenchmarks and serverless functiosn to evaluate interesting metrics and characterics of a serverless runtime. An example would be a flexible and configurable workload generator, based on JMeter or a similar system, to measure throughput, scalability, and the elasticity of the platform when varying workload. Do you have another idea for an interesting experiment? Let us know!
* **Expected outcome**: Contributing to SeBS complete, end-to-end performance experiments.
* **Skills required**: Python. Basic experience with performance measurements and statistics is expected.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number and scope of experiments).
* **Difficulty** - Medium/Hard.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [SeBS] Benchmarking serverless applications
* **Description**: In SeBS, we focus on serverless functions and workflows. However, serverless is a rapidly changing field and a new trend is building entire applications from serverless functions. These include for example using [various cloud triggers to compose functions](https://github.com/joe4dev/trigger-bench/) and porting [microservice benchmarks](https://github.com/delimitrou/DeathStarBench) to serverless. Users of SeBS would greatly benefit from being able to benchmark such complex applications and understand performance bottlenecks of FaaS platforms. Based on existing open-source implementations, one could propose representative applications covering new, exciting use cases of serverless.
* **Expected outcome**: Contributing to SeBS two-three benchmarks covering the open-source applications, with documentation, automatic invocation, and performance metrics. 
* **Skills required**: Python, Docker, C++/Go. Basic experience with cloud storage, APIs and RPC will be necessary.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Hard.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [rFaaS] Libfabric for fast function invocations
* **Description**: rFaaS implements function invocations with single-digit microsecond latency by using _ibverbs_ for communication over RDMA-capable networks. To support networks other than InfiniBand and RoCE, we started an implementation that uses _libfabric_, a higher-level networking library, and targets the Cray GNI network communication. The major goal of the project would be to refactor the existing codebase into two, compatible implementations that use either _ibverbs_ or _libfabric_. However, not all users of rFaaS have access to such network device. Thus, the second goal would be support a larger variety of networks by tuning the libfabric configurationt for protocols such as TCP or AWS EFA. 
* **Expected outcome**: A pull request with a refactored implementation of libfabric port, including configuration for endpoints such as TCP, ibverbs, and AWS EFA.
* **Skills required**: C++, network programming.
* **Project size** - 350 hours (large).
* **Difficulty** - Hard.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), Marcin Chrapek (marcin.chrapek [at] inf [.] ethz [.] ch).
* **Entry task** - contribute a PR to one of the issues marked as "good first issue".

#### [FaaSKeeper] Using serverless ZooKeeper in Apache projects
* **Description**: FaaSKeeper implements standard ZooKeeper functionalities and includes a new client for Python applications. ZooKeeper has been used by many Java and Scala applications in the Apache project, e.g., Kafka and HBase. Sicne they use a limited set of features that might be covered by FaaSKeeper, demonstranting integration of our function-based implementation would be a significant improvement to the project. The goal of the project would be to identify a relevant project(s) that could use FaaSKeeper instead of ZooKeeper, define the set of API calls that have to be implemented, and propose a new Java client library that offloads ZooKeeper calls to the REST cloud API instead of using ZooKeeper protocol.
* **Expected outcome**: New client library exposed to Java applications, implementation of missing API calls (if needed), and demonstration of succesful integration into a larger open-source application using ZooKeeper.
* **Skills required**: Python, Java, and basic understanding of ZooKeeper. Experience with cloud REST APIs might be useful.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Hard.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Deploy FaaSKeeper and execute unit tests.

#### [FaaSKeeper] Multi-cloud serverless ZooKeeper
* **Description**: The primary implementation of FaaSKeeper targets the AWS cloud. However, the system does not rely on a single cloud system and its design is cloud-agnostic (please check the paper preprint for details). The goal of the project would to port existing function code into Azure and Google clouds, by finding corresponding storage, queue, and database services, verifying their limitations and capabilities, and evaluating the performance of new implementaton.
* **Expected outcome**: Contributing a port of existing implementation the the Azure and Google clouds with benchmarks for latency, througput, batching and storage systems.
* **Skills required**: Python, basic experience with cloud is expected (functions, object storage, databases). Experience with the Serverless framework or AWS CloudFormation templates will be helpful.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Hard.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Deploy FaaSKeeper and execute unit tests.

#### [FMI] Optimized and multi-cloud serverless collectives
* **Description**: FMI brings collective operations and point-to-point communication to serverless functions, using cloud storage and TCP connections with NAT hole punching. However, the primary implementation of FMI targets the AWS cloud. The first goal of the project would be porting to a new cloud, such as Google Cloud Functions. The second goal would be optimizing communication. For example, multi-core functions on AWS Lambda allow to execute multiple function workers as threads. There, we can use the local shared memory environment for communication. Another example would be implementing variants of standard and proven collective communication algorithms that target communication on very small (latency-bound) and very-large messages (bandwidth-bound).
* **Expected outcome**: Contributing a port of existing implementation to another cloud, and implementing selected optimizations.
* **Skills required**: C++, network programming, basic experience with cloud is expected (functions, object storage, databases).
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Hard.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Implement and deploy simple serverless application using FMI.

#### [PraaS] Bringing shared-memory environments to serverless processes



### Data-Centric Programming

Introduction to DaCe

* [Project 1](#project-1)
* [Project 2](#project-2)

#### Project 1

#### Project 2

### Project Template

* Descripton
* Expected outcome
* Skills required and preferred - languages, technologies, experience
* Project size - 175 hours (medium) or 350 hours (large)
* Difficulty - easy, medium, difficult, very challenging
* Mentor(s) - please include email address! You can use a picture or replace some characters to avoid spam filters
* Entry task - you are encouraged to define an entry-level task that students should accomplish, e.g., fixing a GitHub issue marked as "good first issue", writing a sample DaCe program.
* Additional informations - such as an opportunity to contribute to a paper

