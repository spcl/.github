
# Google Summer of Code (GSoC) 2025

The SPCL group applied as an organization to the Google Summer of Code (GSoC) program
for our open-source projects in data-centric programming and serverless computing.
You can find here student project proposals, advice on applying, and introductions to
each project to start using our software.

Learn more on how to apply and write your proposal from the [contributor guideline](gsoc_application.md). You will also find there the proposal template. Get get in touch with mentors and discuss the project ideas using the provided email address and reach out to them on [our Mattermost server](https://chat.spcl.inf.ethz.ch/signup_user_complete/?id=6iq1jfforpf9tyhdmffi57zpxw) - join the public **Google Summer of Code*** channel.

## (Tentative) Project Ideas

Our project ideas are grouped into two categories: [**serverless computing**](#serverless) and [**data-centric programming framework**](#data-centric-programming).

### Serverless

At SPCL, we develop several open-source projects that target Function-as-a-Service (FaaS),
a new cloud paradigm concerned with writing stateless and _serverless_ functions.
Our benchmarking suite [SeBS](https://github.com/spcl/serverless-benchmarks) provides automatic build, deployment and invocations of representative serverless functions on several commercial and open-source FaaS platforms.
We published and develop a serverless ZooKeeper implementation [FaaSKeeper](https://github.com/spcl/faaskeeper),
a high-performance and RDMA-based serverless platform [rFaaS](https://github.com/spcl/rFaaS),
a serverless collectives library [FMI](https://github.com/spcl/FMI) for parallel and distributed applications,
system for serverless processes [PraaS](https://github.com/spcl/PraaS), and GPU runtime for serverless [MIGnificient](https://github.com/spcl/MIGnificient).

* [[SeBS] Website for experimental results](#sebs-website-for-experimental-results)
* [[SeBS] Keeping up with clouds](#sebs-keeping-up-with-the-clouds)
* [[SeBS] Supporting new serverless platforms](#sebs-supporting-new-serverless-platforms)
* [[SeBS] Adding new serverless benchmarks](#sebs-new-serverless-benchmarks)
* [[SeBS] Support for new performance experiments](#sebs-new-performance-experiments)
* [[SeBS] Adding serverless applications as benchmarks](#sebs-benchmarking-serverless-applications)
* [[rFaaS] Serverless MPI functions](#rfaas-serverless-mpi-functions)
* [[FaaSKeeper] Using serverless ZooKeeper in Apache projects](#faaskeeper-using-serverless-zookeeper-in-apache-projects)
* [[FMI] Optimized and multi-cloud serverless collectives](#fmi-optimized-and-multi-cloud-serverless-collectives)

#### [SeBS] Website for experimental results
* **Description**: SeBS allows the generation of many experimental results in performance and container management, and soon, we will have full support for workflows and communication benchmarks. We are also working on gathering long-term performance measurements for large serverless applications. However, we are missing a good website interface to present these performance measurements to the users. In this project, we want to deploy the first version of a website that can display results obtained with SeBS. The website should use an existing library/solution to dynamically create plots and change between scenarios (language, memory size, experiment, platform). The website should pull data from a predefined place, e.g., a GitHub repository. Ideally, the plots should be interactive, e.g., displaying data point values, zooming in/out, and removing certain features from the plot (e.g., displaying only selected memory configurations). The website should be extensible to allow more complex datasets in the future, e.g., supporting large applications that consist of many functions. A website that we can host on github.io would be a huge plus (restrictions on the dynamic content, something like Hugo or Jekyll).
* **Expected outcome**: Contributing to SeBS support for new runtimes and platforms, ensuring that existing workloads work correctly there.
* **Skills required**: frontend and backend development.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number of features for the website). 
* **Difficulty** - Medium.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Create a convincing idea draft for the website or contribute a PR to one of the issues marked as "good first issue".

#### [SeBS] Keeping up with the clouds
* **Description**: In SeBS, we support AWS Lambda, Google Cloud Functions, Azure Functions, and OpenWhisk. Since the original release of SeBS, we have seen a lot of changes: growing popularity of ARM functions on AWS, new Azure Functions runtime versions, Google Cloud Functions version 2, and Knative becoming one of the most popular open-source serverless platforms. Furthermore, SeBS lacks support for deploying functions as containers instead of code packages. Adding support for new runtimes and platforms would help SeBS stay usable and competitive in the changing world of clouds.
* **Expected outcome**: Contributing to SeBS support for new runtimes and platforms, ensuring that existing workloads work correctly there.
* **Skills required**: Python, Docker. Basic experience with cloud is expected (functions, object storage, databases). Experience with Node.js be helpful for some of the benchmarks.
* **Project size** - 90 hours (small) or 175 hours (medium), depending on the project scope. 
* **Difficulty** - Easy/Medium.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

#### [SeBS] Supporting new serverless platforms
* **Description**: In SeBS, we support AWS Lambda, Google Cloud Functions, Azure Functions, and OpenWhisk. We would like to extend the support with new serverless platforms, particularly focusing on the quickly growing KNative project. This requires adding new benchmark wrappers, packaging code in the container format expected by Knative, and interfacing with their metrics system to gather measurement data. In addition, we want to complete the support for the Fission platform (see issue #61).
* **Expected outcome**: Contributing to SeBS support for new open-source platforms, ensuring that existing workloads work correctly there.
* **Skills required**: Python, Docker. Basic experience with cloud is expected (functions, object storage, databases). Experience with Node.js be helpful for some of the benchmarks.
* **Project size** - 90 hours (small) or 175 hours (medium), depending on the project scope. 
* **Difficulty** - Easy/Medium.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - Contribute a PR to one of the issues marked as "good first issue".

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

#### [rFaaS] Serverless MPI functions
* **Description**: The HPC community has been working on supporting malleable and evolving applications in MPI, i.e., applications that require dynamic adjusting of the number of workers. Examples include Flex-MPI and invasive MPI. Serverless functions could be a perfect runtime for such a task - they can be allocated and removed on-the-fly, aiding the elasticity of MPI applications. However,  MPI runtimes are tightly coupled with batch systems, and reimplementing the MPI interface with a new serverless-aware library would prevent us from using optimized communication methods. Instead, in this project, we want to investigate an alternative approach - analyze the process runtime of an open-source MPI implementation, such as the PMI component of OpenMPI. We want to replace the process management with an experimental prototype that will allocate MPI processes as rFaaS functions. With initialized processes and communication, functions can execute MPI code and benefit from tuned implementations of MPI collectives.
* **Expected outcome**: A prototype implementation that can execute a simple MPI application by allocating MPI processes as rFaaS functions.
* **Skills required**: C++, HPC, a bit of hacking to get into OpenMPI/MPICH internals.
* **Project size** - 350 hours (large).
* **Difficulty** - Difficult.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com).
* **Entry task** - build rFaaS and test it with SoftRoCE.
*
#### [FaaSKeeper] Using serverless ZooKeeper in Apache projects
* **Description**: FaaSKeeper implements standard ZooKeeper functionalities and includes a new client for Python applications. ZooKeeper has been used by many Java and Scala applications in the Apache project, e.g., Kafka and HBase. Since they use a limited set of features that might be covered by FaaSKeeper, demonstrating the integration of our function-based implementation would be a significant improvement to the project. The goal of the project would be to identify a relevant project(s) that could use FaaSKeeper instead of ZooKeeper, define the set of API calls that have to be implemented, and propose a new Java client library that offloads ZooKeeper calls to the REST cloud API instead of using ZooKeeper protocol.
* **Expected outcome**: New client library exposed to Java applications, implementation of missing API calls (if needed), and demonstration of succesful integration into a larger open-source application using ZooKeeper.
* **Skills required**: Python, Java, and basic understanding of ZooKeeper. Experience with cloud REST APIs might be useful.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium/Difficult.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com, [mcopik @ GitHub](https://github.com/mcopik/)), Alexandru Calotoiu (alexandru.calotoiu [at] inf.ethz [.] ch)
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

[DaCe](https://github.com/spcl/dace), or the Data-Centric Parallel Programming Framework, is a framework geared towards optimizing the data movement behavior of applications, a factor that limits the performance and efficiency of many large, real-world applications. The framework started at SPCL and is now being actively developed by multiple research groups around the world. 
DaCe takes code written in Python and other programming languages, and translates it to highly optimized CPU, GPU, or FPGA programs through the use of a [graphical intermediate program representation](https://spcldace.readthedocs.io/en/latest/sdfg/ir.html#the-language).
This intermediate representation exposes which and how much data is moved in a program, and allows a programmer to interactively optimize the application by applying simple, pre-defined transformations to its dataflow.
DaCe comes with a Visual Studio Code extension that lets you interact with programs and optimize them. You can see a demonstration of this [here](https://github.com/spcl/dace-vscode).
DaCe is used in a variety of applications, including weather and climate prediction models, quantum transport simulations, and fast machine learning operators.

* [[DaCe] Generating fast CPU code with vectorization](#dace-generating-fast-cpu-code-with-vectorization)

#### [DaCe] Generating Fast CPU Code with Vectorization
* **Description**: Modern processors offer extensive vectorization options. Writing code in vectorized SIMD notation often involves additional development work targeted towards particular hardware, imposing significant portability and maintainability challenges. Vectorization libraries, such as [SLEEF](https://github.com/shibatch/sleef), [Highway](https://github.com/google/highway), [Vc](https://github.com/VcDevel/Vc), and others, implement vectorized versions of standard C operations and math functions, providing a simpler and more portable alternative. The goal of this project is to leverage one of those libraries to generate *fast* vectorized CPU code in the [DaCe](https://spcldace.readthedocs.io/en/latest/) framework. You will first choose a vectorization library and justify why it is the right choice. Then, you will ensure DaCe generates code that calls vectorized versions of operators (unary, binary, etc.) and math functions. Throughout the project, you will use [NPBench](https://github.com/spcl/npbench) to test the performance of the generated code on 52 scientific computing benchmarks. Successfully implementing a project like this might boost the performance of the benchmarks by 2-4x, with no changes to the original code!
* **Expected outcome**: Implementing vectorized operations to allow DaCe to take advantage of SIMD instructions on new CPUs (and maybe GPUs...) that the chosen open source library offers.
* **Skills required**: Python and C++. Basic experience with performance measurements and statistics is beneficial.
* **Project size** - 350 hours (large).
* **Difficulty** - Medium.
* **Mentor(s)**: Tal Ben-Nun (talbn [at] llnl [.] gov)
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

