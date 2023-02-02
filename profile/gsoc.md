
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

At SPCL, we develop several open-source projects: our benchmarking suite [SeBS](github.com/spcl/serverless-benchmarks),
a serverless ZooKeeper implementation [FaaSKeeper](github.com/spcl/faaskeeper),
high-performance and RDMA-based serverless platform [rFaaS](github.com/spcl/rFaaS),
serverless collectives

* [Benchmarking serverless platforms with SeBS](#benchmarking-serverless-platforms-with-sebs)

#### Benchmarking serverless platforms with SeBS
* **Description**: SeBS supports automatic benchmarking of serverless functions on AWS Lambda, Azure Functions, Google Cloud Functions, and OpenWhisk. We would like to expand SeBS with support for new platforms, such as Fission, Knative, Cloudflare Workers, etc. The new functionality would integrate the platform-specific interface into SeBS, allowing our experiments to automatically deploy and invoke functions.
* **Expected outcome**: Adding to SeBS interface to automatically deploy and execute functions on new serverless platforms.
* **Skills required**: Python, Docker. Experience with Kubernetes would be helpful.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number of platforms).
* **Difficulty** - easy.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - contribute a PR to one of the issues marked as "good first issue".

#### New serverless benchmarks in SeBS
* **Description**: In SeBS, we provide a representative set of functions and we have an ongoing work towards serverless workflows. The serverless field is constantly changing, and new workloads are constantly being implemented. We would like to extend our benchmarking suite with new function candidates, such as utility functions (PDF generation, antivirus scanning) or scientific benchmarks; new invocation types (functions invoked on changes in object storage); and new workflows.
* **Expected outcome**: Contributing to SeBS new benchmarking functions, triggers, and workloads that succesfully execute on already supported platforms.
* **Skills required**: Python, Docker. Basic experience with cloud is expected (functions, object storage, databases). Experience with Node.js and Go might be helpful for some of the benchmarks.
* **Project size** - 175 hours (medium) or 350 hours (large), depending on the project scope (number of benchmarks).
* **Difficulty** - medium.
* **Mentor** - Marcin Copik (mcopik [at] gmail [.] com), [mcopik @ GitHub](https://github.com/mcopik/)
* **Entry task** - contribute a PR to one of the issues marked as "good first issue".

#### New performance experiments in SeBS

#### Benchmarking serverless applications

#### Libfabric for fast function invocations in rFaaS

#### Using FaaSKeeper in Hadoop

#### Optimized and multi-cloud serverless collectives

#### Bringing shared-memory environments to serverless processes


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

