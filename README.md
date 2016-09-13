<img src='doc/GH_logo.png' width='250' height='250' title='Pachyderm'> 

[![GitHub release](https://img.shields.io/github/release/pachyderm/pachyderm.svg?style=flat-square)](https://github.com/pachyderm/pachyderm/releases)
[![GitHub license](https://img.shields.io/github/license/pachyderm/pachyderm.svg?style=flat-square)](https://github.com/pachyderm/pachyderm/blob/master/LICENSE)
[![GoDoc](https://godoc.org/github.com/pachyderm/pachyderm?status.svg)](https://godoc.org/github.com/pachyderm/pachyderm/src/client)
[![Slack](http://slack.noms.io/badge.svg)](http://slack.pachyderm.io)

# A Containerized Data Lake
Pachyderm is [Git for Data Science](pachyderm.io/pfs.html). We offer complete version control for data and give your data scientists the same first-class development tools as software developers. Pachyderm is ideal for building machine learning pipelines and ETL workflows because we version and track track every model/output directly to the raw input datasets that created it (aka: [Provenance](pachyderm.readthedocs.io/advanced/provenance.html)). 

Pachyderm is built on Docker and Kubernetes. Since everything in Pachyderm is a container, data scientists can use any languages or libraries they want (e.g. R, Python, OpenCV, etc) without any additional infrastructure overhead. 

* [Getting Started](http://pachyderm.readthedocs.io/)
* [What is Pachyderm?](#what-is-pachyderm)
* [What's new about Pachyderm? (How is it different from Hadoop?)](#whats-new-about-pachyderm-how-is-it-different-from-hadoop)
* [Contributing](#contributing)
* [Join Us](#join-us)
* [Usage Metrics](#usage-metrics)

### Getting Started

Refer to our [developer docs](http://pachyderm.readthedocs.io) to get started.

### What is Pachyderm?

Pachyderm is a software platform the supports the storage and processing of large data sets.
Pachyderm is inspired by the Hadoop ecosystem but _shares no code_ with it.
Instead, we leverage the container ecosystem to provide the broad functionality
of Hadoop with the ease of use of Docker.

### What's new about Pachyderm? (How is it different from Hadoop?)

There are two bold new ideas in Pachyderm:

- Containers as the core processing primitive
- Version Control for data

These ideas lead directly to a system that's much more powerful, flexible and easy to use. 

To process data, you simply create a containerized program which reads and writes to the **local filesystem**. You can use _any_ tools you want because it's all just going in a container! Pachyderm will take your container and inject data into it by way of a FUSE volume. We'll then automatically replicate your container, showing each copy a different chunk of data. With this technique, Pachyderm can scale any code you write to process up to petabytes of data (Example: [distributed grep](https://github.com/pachyderm/pachyderm/tree/master/examples/fruit_stand)).

Pachyderm also version controls all data using a commit-based distributed
filesystem (PFS), similar to what git does with code. Version control for data
has far reaching consequences in a distributed filesystem. You get the full
history of your data, it's much easier to collaborate with teammates, and if
anything goes wrong you can revert _the entire cluster_ with one click!

Version control is also very synergistic with our containerized processing
engine. Pachyderm understands how your data changes and thus, as new data
is ingested, can run your workload on the _diff_ of the data rather than the
whole thing. This means that there's no difference between a batched job and
a streaming job, the same code will work for both!

### Contributing

To get started, sign the [Contributor License Agreement](https://pachyderm.wufoo.com/forms/pachyderm-contributor-license-agreement).

Send us PRs, we would love to see what you do!

### Join Us

WE'RE HIRING! Love Docker, Go and distributed systems? Learn more about [our team](http://www.pachyderm.io/jobs.html) and email us at jobs@pachyderm.io.

### Usage Metrics

Pachyderm automatically reports anonymized usage metrics. These metrics help us
understand how people are using Pachyderm and make it better.  They can be
disabled by setting the env variable `METRICS` to `false` in the pachd
container.
