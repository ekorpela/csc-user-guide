# Data analysis guide

The purpose of this guide is to help you in choosing the right tools and environment for your data analysis.  In addition, CSC organises a [wide variety of training courses](https://www.csc.fi/web/training), many of which are related to data analytics and machine learning in CSC's computing environments.  Finally, CSC's specialists are happy to help with all aspects of your data driven research, and can be contacted via the [CSC Service Desk](https://www.csc.fi/contact-info).

## Getting started

To get started, you need to:

- have a [CSC account](../../accounts/how-to-create-new-user-account.md)
- be member of a CSC project, either by [creating a new project](../../accounts/how-to-create-new-project.md) or joining an existing project, .e.g. by asking the [project manager to add you](../../accounts/how-to-add-member-to-project.md)

Finally, the project needs to have [access to the services](../../accounts/how-to-add-service-access-for-project.md) you will use.  More on our services below, and when you might use them.

## CSC's services

Below is a short glossary of CSC's services that are most relevant for data analysis.

[**Puhti**](../../computing/overview.md) is CSC's supercomputer where most computing should be done.  [Puhti has a large set of pre-installed applications](../../apps/index.md), and scales up to very computing heavy tasks, including GPU-based processing.

[**Allas**](../../data/Allas/index.md) is CSC's data storage service.  If you have big datasets or need to share data with people outside of your project, you should consider using Allas.

[**Pouta**](../../cloud/pouta/index.md) is CSC's cloud service where you can create your own virtual server.  This gives you more control over the computing environment, but may not be suitable for very heavy computing tasks.  Pouta is also more suitable for processing sensitive data, especially the ePouta variant.

[**Rahti**](../../cloud/rahti/index.md) is CSC's container cloud.  Here you can easily create virtual applications based on container images.

[**Notebooks**](https://notebooks.csc.fi/) is a great service if you just want to run a quick analysis directly in your web browser. Notebooks supports Jupyter with Python tools for data analysis and machine learning, and also RStudio.

## Example use cases

### Getting into data-driven research

*You have been dabbling in Excel or SPSS but now you are looking for more powerful ways to handle your data.*

<!-- WHO: Anni

A great way to start with data analytics is to attend a course.
You can check out upcoming courses from [CSC training website](https://www.csc.fi/web/training) .
Also, CSC has some training materials that are suitable for self-learning, such as [the introductory R course](https://github.com/csc-training/R-for-beginners).
If you are in the field of bioinformatics, you might also want to check out the [chipster platform](https://chipster.csc.fi/)

There are also plenty of data science available online, some popular resources include [udemy](https://www.udemy.com/courses/development/data-science/), and
[coursera](https://www.coursera.org/browse/data-science).

[minimum] Courses: R, Python, ...
links to Notebooks course?
Chipster

[longer] Basics
use case: user just has some data in Excel -> use R !
link to “Easy-R” guide (needs creating) 
-->

### Scaling up from your laptop (beginner)

*You have been running analyses in R or Python for some time already, but you have reached the limits of your own laptop or desktop computer. Perhaps you need more memory or faster processing?*

In most cases, the next step would be to move to CSC's supercomputer Puhti, which is a high performance computing (HPC) cluster. That means it's not one computer, but a collection of many computers. Users access the front-end server (login node) of Puhti, where they can submit computing jobs to a queuing system which takes care of distributing them to the cluster's different computers (compute nodes).  Please read the [instructions on how to access Puhti](../../computing/overview.md), and [how to submit computing jobs to Puhti's queuing system](../../computing/running/getting-started.md).

Puhti has a [large selection of scientific computing applications pre-installed](../../apps/index.md), including [R](../../apps/r-env.md) and [Python libraries for data analysis](../../apps/python-data.md).  If you find something missing, don't hesitate to contact our [Service Desk](https://www.csc.fi/contact-info).

As Puhti is a shared computing environment, users are restricted in what they can do, for example when it comes to installing customized software or processing sensitive data.  In some cases, it might make sense to instead use [**Pouta**](../../cloud/pouta/index.md) to create your own virtual server.  This gives you more control over the computing environment, but may not be suitable for very heavy computing tasks.  Another option is [**Rahti**](../../cloud/rahti/index.md), where you can create virtual machines based on container images.  See some examples of [how to deploy machine learning models on Rahti](https://github.com/CSCfi/rahti-ml-examples).

<!-- WHO: Mats, Jesse -->

### Heavy computing needs (advanced)

*You are already an expert, but you have outgrown the resources of your local institution.*

If you need to heavily parallelise your computing, or for example use GPU-accelerated processing, Puhti is the right answer (see instructions in the above section).

For GPU-accelerated machine learning, we support [TensorFlow](../../apps/tensorflow.md), [PyTorch](../../apps/pytorch.md), [MXNET](../../apps/mxnet.md) and [RAPIDS](../../apps/rapids.md).  All GPU nodes have [fast local NVME storage](../../computing/running/creating-job-scripts.md#local-storage) which is particularly useful when you need to read a lot of files for training your machine learning model.

Multi-GPU jobs are also supported, and for large jobs requiring more than 4 GPUs we recommend Horovod which is supported for TensorFlow and PyTorch (see application pages for instructions).

If you are using R for data analysis, we also support [parallel batch jobs in R](../../apps/r-env.md#parallel-batch-jobs). Depending on your needs, many types of parallel computing are possible using R. Further to jobs employing multiple processors (cores), it is possible to run array jobs where an analysis is split into many subtasks. For analyses requiring multiple nodes, R also supports several types of Message Passing Interface (MPI)-based jobs.

<!-- WHO: Mats 
Python: GPU, local scratch, Horovod etc

WHO: Jesse

-->

<!-- [minimum] GPU work, e.g. deep learning (link) -->

<!-- [minimum] Parallel jobs in cluster environment (link) -->

### Big data processing (advanced)

You can use Rahti for example running [big data analytics and machine learning jobs on scalable Apache Spark cluster](../../apps/spark.md).

<!-- [minimum] Working with large data sets, e.g.  -->

<!-- Spark / Hadoop, Kafka (incl. ML perspective) -->

<!--     use case: I’ve got a lot of data, options:  -->

<!-- use Spark, Kafka if [something] (tree schematic?) -->

<!-- big datasets considerations in cluster: Allas, many small files no-no -->

<!-- [longer article, or part of other article] big datasets in cluster (e.g. TFRecords, Allas, etc) -->

<!-- ML deployment in Rahti, “I have trained models in Puhti, how can I deploy them for use by my colleagues?”  // Mats -->

### Course environments (for teachers)

*You are teaching a course that needs complex computing environments for its exercises but you do not want to spend valuable course time on debugging installation errors.* 

Consider using CSC's [Notebooks](https://notebooks.csc.fi/) service that contains easy-to-use environments for working with data and programming. The course environments support Jupyter, Python (including many machine learning libraries), R / RStudio Server and Spark.

If you are planning to use Notebooks, please remember to submit a notification about your course requirements using [this online form](https://www.webropolsurveys.com/S/84118B6BD6E97501.par).

CSC's collection of [GitHub repositories](https://github.com/csc-training) for training purposes can also be a valuable resource for course planning and sharing teaching materials with course participants.

<!-- WHO: Minna, Jesse  -->

<!-- Notebooks (Rahti in longer article) -->

<!-- CSC GitHub -->