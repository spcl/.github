
# Google Summer of Code (GSoC) 2023

The SPCL group applied as an organization to the Google Summer of Code (GSoC) program
for our open-source projects in data-centric programming and serverless computing.
You can find here student project proposals, advice on applying, and introductions to
each project to start using our software.

Learn more on how to apply and write your proposal from the [contributor guideline](gsoc_application.md). You will also find there the proposal template. Get get in touch with mentors and discuss the project ideas using the provided email address and reach out to them on [our Mattermost server](https://chat.spcl.inf.ethz.ch/signup_user_complete/?id=6iq1jfforpf9tyhdmffi57zpxw) - join the public **Google Summer of Code*** channel.

## Project Ideas

Our project ideas are grouped into two categories: [**serverless computing**](#serverless) and [**data-centric programming framework**](#data-centric-programming).

### Serverless

At SPCL, we develop several open-source projects that target Function-as-a-Service (FaaS),
a new cloud paradigm concerned with writing stateless and _serverless_ functions.
Our benchmarking suite [SeBS](https://github.com/spcl/serverless-benchmarks) provides automatic build, deployment and invocations of representative serverless functions on several commercial and open-source FaaS platforms.
We published and develop a serverless ZooKeeper implementation [FaaSKeeper](https://github.com/spcl/faaskeeper),
a high-performance and RDMA-based serverless platform [rFaaS](https://github.com/spcl/rFaaS),
and a serverless collectives library [FMI](https://github.com/spcl/FMI) for parallel and distributed applications.

* [[SeBS] Adding new serverless benchmarks](#sebs-new-serverless-benchmarks)
* [[SeBS] Support for new performance experiments](#sebs-new-performance-experiments)
* [[SeBS] Adding serverless applications as benchmarks](#sebs-benchmarking-serverless-applications)
* [[rFaaS] Libfabric for fast function invocations](#rfaas-libfabric-for-fast-function-invocations)
* [[FaaSKeeper] Using serverless ZooKeeper in Apache projects](#faaskeeper-using-serverless-zookeeper-in-apache-projects)
* [[FaaSKeeper] Multi-cloud serverless ZooKeeper](#faaskeeper-multi-cloud-serverless-zookeeper)
* [[FMI] Optimized and multi-cloud serverless collectives](#fmi-optimized-and-multi-cloud-serverless-collectives)

#### [SeBS] New serverless benchmarks
* **Description**: In SeBS, we provide a representative set of functions, and we have developed a set of serverless workflows that will be included in the upcoming release. However, the serverless field is constantly changing, and new types of applications are being "FaaS-ified". Therefore, we would like to extend our benchmarking suite with new function candidates, such as utility functions (PDF generation, antivirus scanning) or scientific benchmarks, new invocation types (functions invoked on changes in object storage), and new workflows.
* **Expected outcome**: Contributing to SeBS new benchmarking functions, triggers, and workloads that succesfully execute on already supported platforms.
* **Skills required**: Python, Docker. Basic experience with cloud is expected (functions, object storage, databases). Experience with Node.js and Go might be helpful for some of the benchmarks.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number of benchmarks).
* **Difficulty** - Easy/Medium.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [SeBS] New performance experiments
* **Description**: SeBS includes automatic experiments that evaluate specific performance features of serverless platforms, such as latency and cost of function invocations or invocation overheads. The goal of the project would be to add new experiments that use microbenchmarks and serverless functions to evaluate interesting metrics and characteristics of a serverless runtime. An example would be a flexible and configurable workload generator, based on JMeter or a similar system, to measure throughput, scalability, and the elasticity of the platform when varying workloads. Another goal would be to extend existing trigger types with storage and queues to understand the latency and throughput of synchronous and asynchronous invocations and measure the latency of pipeline invocations. Do you have another idea for an interesting experiment? Let us know!
* **Expected outcome**: Contributing to SeBS complete, end-to-end performance experiments.
* **Skills required**: Python. Basic experience with performance measurements and statistics is expected.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number and scope of experiments).
* **Difficulty** - Medium/Difficult.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com, [mcopik @ GitHub](https://github.com/mcopik/)), Alexandru Calotoiu (alexandru.calotoiu [at] inf.ethz [.] ch)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [SeBS] Benchmarking serverless applications
* **Description**: In SeBS, we focus on serverless functions and workflows. However, serverless is a rapidly changing field, and a new trend is building entire applications from serverless functions. These include, for example, using [various cloud triggers to compose functions](https://github.com/joe4dev/trigger-bench/) and porting [microservice benchmarks](https://github.com/delimitrou/DeathStarBench) to serverless. Users of SeBS would greatly benefit from being able to benchmark such complex applications and understand the performance bottlenecks of FaaS platforms. Based on existing open-source implementations, one should propose representative applications covering new, exciting use cases of serverless.
* **Expected outcome**: Contributing to SeBS two-three benchmarks covering the open-source applications, with documentation, automatic invocation, and performance metrics. 
* **Skills required**: Python, Docker, C++/Go. Basic experience with cloud storage, APIs and RPC will be necessary.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Difficult.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com, [mcopik @ GitHub](https://github.com/mcopik/))
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [rFaaS] Libfabric for fast function invocations
* **Description**: rFaaS implements function invocations with single-digit microsecond latency by using _ibverbs_ for communication over RDMA-capable networks. To support networks other than InfiniBand and RoCE, we started an implementation that uses _libfabric_, a higher-level networking library, and targets the Cray GNI network communication. The project's primary goal would be to refactor the existing codebase into two compatible implementations that use either _ibverbs_ or _libfabric_. However, not all users of rFaaS have access to a such network device. Thus, the second goal is to support a larger variety of networks by tuning the libfabric configuration for protocols such as TCP or AWS EFA.
* **Expected outcome**: A pull request with a refactored implementation of libfabric port, including configuration for endpoints such as TCP, ibverbs, and AWS EFA.
* **Skills required**: C++, network programming.
* **Project size** - 350 hours (large).
* **Difficulty** - Difficult.
* **Mentor** - Marcin Chrapek (marcin.chrapek [at] inf [.] ethz [.] ch), Marcin Copik (mcopik [at] gmail [.] com).
* **Entry task** - contribute a PR to one of the issues marked as "good first issue".

#### [FaaSKeeper] Using serverless ZooKeeper in Apache projects
* **Description**: FaaSKeeper implements standard ZooKeeper functionalities and includes a new client for Python applications. ZooKeeper has been used by many Java and Scala applications in the Apache project, e.g., Kafka and HBase. Since they use a limited set of features that might be covered by FaaSKeeper, demonstrating the integration of our function-based implementation would be a significant improvement to the project. The goal of the project would be to identify a relevant project(s) that could use FaaSKeeper instead of ZooKeeper, define the set of API calls that have to be implemented, and propose a new Java client library that offloads ZooKeeper calls to the REST cloud API instead of using ZooKeeper protocol.
* **Expected outcome**: New client library exposed to Java applications, implementation of missing API calls (if needed), and demonstration of succesful integration into a larger open-source application using ZooKeeper.
* **Skills required**: Python, Java, and basic understanding of ZooKeeper. Experience with cloud REST APIs might be useful.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Difficult.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com, [mcopik @ GitHub](https://github.com/mcopik/)), Alexandru Calotoiu (alexandru.calotoiu [at] inf.ethz [.] ch)
* **Entry task** - Deploy FaaSKeeper and execute unit tests.

#### [FaaSKeeper] Multi-cloud serverless ZooKeeper
* **Description**: The primary implementation of FaaSKeeper targets the AWS cloud. However, the system does not rely on a single cloud system, and its design is cloud-agnostic (please check the paper preprint for details). The project's goal would be to port existing function code into Azure and Google clouds by finding corresponding storage, queue, and database services, verifying their limitations and capabilities, and evaluating the performance of new implementations.
* **Expected outcome**: Contributing a port of existing implementation the the Azure and Google clouds with benchmarks for latency, througput, batching and storage systems.
* **Skills required**: Python, basic experience with cloud is expected (functions, object storage, databases). Experience with the Serverless framework or AWS CloudFormation templates will be helpful.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Difficult.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/), Alexandru Calotoiu (alexandru.calotoiu [at] inf.ethz [.] ch)
* **Entry task** - Deploy FaaSKeeper and execute unit tests.

#### [FMI] Optimized and multi-cloud serverless collectives
* **Description**: FMI brings collective operations and point-to-point communication to serverless functions, using cloud storage and TCP connections with NAT hole punching. However, the primary implementation of FMI targets the AWS cloud. The first goal of the project would be porting to a new cloud, such as Google Cloud Functions. The second goal would be optimizing communication. For example, multi-core functions on AWS Lambda allow for the execution of multiple function workers as threads. There, we can use the local shared memory environment for communication. Another example would be implementing variants of standard and proven collective communication algorithms that target communication on very small (latency-bound) and very-large messages (bandwidth-bound). [This paper](https://web.cels.anl.gov/~thakur/papers/ijhpca-coll.pdf) is a good starting point on various communication algorithms.
* **Expected outcome**: Contributing a port of existing implementation to another cloud, and implementing selected optimizations.
* **Skills required**: C++, network programming. Basic experience with cloud (functions, object storage, databases) and with parallel algorithms is expected.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Difficult.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/), Alexandru Calotoiu (alexandru.calotoiu [at] inf.ethz [.] ch)
* **Entry task** - Implement and deploy simple serverless application using FMI.

### Data-Centric Programming

At SPCL, we develop a programming framework that is geared towards optimizing the data movement behavior of applications, a factor that limits the performance and efficiency of many large, real-world applications.
[DaCe](https://github.com/spcl/dace), or the Data-Centric Parallel Programming Framework, takes code written in Python and other programming languages, and translates it to highly optimized CPU, GPU, or FPGA programs through the use of a [graphical intermediate program representation](https://spcldace.readthedocs.io/en/latest/sdfg/ir.html#the-language).
This intermediate program representation exposes where a program moves how much data and allos a programmer to interactively optimize the application by applying simple, pre-defined "transformations" from a library.
DaCe comes with a Visual Studio Code extension that lets you interact with programs and optimize them. You can see a demonstration of this [here](https://github.com/spcl/dace-vscode).

* [[Radio-DaCe] Data-Centric Frequency Domain Optimizations](#radio-dace-data-centric-frequency-domain-optimizations)
* [[SLEEF in DaCe] Vectorization using SLEEF in DaCe](#sleef-in-dace-vectorization-using-sleef-in-dace)
* [[Mpi4py in DaCe] Add support for Mpi4py in DaCe](#mpi4py-in-dace-add-support-for-mpi4py-in-dace)

#### [Radio-DaCe] Data-Centric Frequency Domain Optimizations
* **Description**: [GNU Radio](https://github.com/gnuradio/gnuradio) is a large, open-source software development toolkit that provides signal processing blocks to implement software defined radios. Today, SDRs are being considered in several scenarios, ranging from 5G wireless mobile networks and Cloud Radio Access Networks, to radar communications. To match the real-time constraints typical of such scenarios, SDRs have stringent requirements in terms of throughput and latency. GNU Radio provides a flowgraph-oriented approach and a comprehensive library of processing blocks that can be readily combined to make complex signal processing applications. The goal of this project is to leverage [DaCe](https://spcldace.readthedocs.io/en/latest/) and its optimization potential to significantly improve the efficiency and performance of complex signal processing pipelines defined in GNU Radio by, among other things, leveraging more degrees of parallelism.
* **Expected outcome**: Implementing existing GNU Radio processing blocks as DaCe libraries and constructing an interface to let DaCe call native GNU Radio processing blocks.
* **Skills required**: Python and C++. Basic experience with performance measurements and statistics is beneficial.
* **Project size** - 350 hours (large).
* **Difficulty** - Difficult.
* **Mentor(s)**: Philipp Schaad (philipp.schaad [at] inf.ethz [.] ch), [phschaad @ GitHub](https://github.com/phschaad), Tiziano De Matteis (tiziano.dematteis [at] inf.ethz [.] ch)
* **Entry task**: Create a simple DaCe program through Python and run it.

#### [SLEEF in DaCe] Vectorization using SLEEF in DaCe
* **Description**: Modern processors offer extensive vectorization options. Writing code that can successfully vectorized often involves additional development work targeted towards particular hardware, imposing significant portability and maintainability challenges. [SLEEF](https://github.com/shibatch/sleef) is a library that implements vectorized versions of standard C math functions, providing a simpler and more portable alternative. The goal of this project is to leverage SLEEF to provide efficient vectorization options within the [DaCe](https://spcldace.readthedocs.io/en/latest/) framework. 
* **Expected outcome**: Implementing SLEEF library node expansions to allow DaCe  to take advantage of the vectorization opportunities that the SLEEF library offers.
* **Skills required**: Python and C++. Basic experience with performance measurements and statistics is beneficial.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium.
* **Mentor(s)**: Alexandru Calotoiu (alexandru.calotoiu [at] inf.ethz [.] ch)
* **Entry task**: Install and run the [NPBench](https://github.com/spcl/npbench) set of benchmarks and run them using DaCe. 

#### [Mpi4py in DaCe] Add support for Mpi4py in DaCe
* **Description**: The Message Passing Interface (MPI) is the uncontested standard for communication in distributed memory systems. While the MPI standard is focused on the C and Fortran, the main language for high performance computing, an increasing number of scientific applications are written in Python. [Mpi4py](https://github.com/mpi4py/mpi4py/) is a package that offers Python bindings for the MPI standard. The goal of this project is to implement support for mpi4py in the [DaCe](https://spcldace.readthedocs.io/en/latest/) framework. 
* **Expected outcome**: Add support for the mpi4py syntax in DaCe. 
* **Skills required**: Python. Basic experience with MPI and performance measurements and statistics is beneficial.
* **Project size** - 350 hours (large).
* **Difficulty** - Difficult.
* **Mentor(s)**: Alexandru Calotoiu (alexandru.calotoiu [at] inf.ethz [.] ch)
* **Entry task**: Install and run the [NPBench](https://github.com/spcl/npbench) set of benchmarks and run them using DaCe. 

### Project Template

* Descripton
* Expected outcome
* Skills required and preferred - languages, technologies, experience
* Project size - 175 hours (medium) or 350 hours (large)
* Difficulty - easy, medium, difficult, very challenging
* Mentor(s) - please include email address! You can use a picture or replace some characters to avoid spam filters
* Entry task - you are encouraged to define an entry-level task that students should accomplish, e.g., fixing a GitHub issue marked as "good first issue", writing a sample DaCe program.
* Additional informations - such as an opportunity to contribute to a paper

