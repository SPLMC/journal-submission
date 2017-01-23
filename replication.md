---
layout: default
title:  Experiment replication
---

For those whom are interested in replicating our experiment, we provide two
alternative environments containing the ReAna-SPL tool, the artifacts of all
evaluated software product lines (including its evolutions) and the scripts for
results analysis. Each alternative and its usage instructions is described
below.

---

## Docker's container

A public [Docker][docker] repository containing the image of the experiment's
environment is available at Docker Hub. It can be accessed directly at the
following URL: [https://hub.docker.com/r/splmc/reana-spl/][reana-docker-repo].

To execute the experiments you must download the environment's image
from ReAna's repository, create a local container (taking the hosting
machine's characteristics into account) and execute the evaluation script inside
the container.  Each step is detailed in the following. 

1. **Downloading the image from Docker Hub:**

In order to download the image from Docker Hub, it is necessary having the
Docker installed and running at the host machine. In case the host machine does
not have the Docker Platform installed, you should follow the install
instructions available [here][docker-download]. 

Once Docker platform is installed and running accordingly, you can download the
image containing the experiment environment by typing the following instruction
at a terminal of the host machine: 

{% highlight shell %}
docker pull splmc/reana-spl:istSubmission
{% endhighlight %}

The image's size is around 526 MB, so the download may take some time depending
on your connection speed. 

{:start="2"}
2. **Creating the container:** 

Before creating the experiment's container it is approppriate to know which are
the host's resources. Docker platform provides the following command for showing
such information at a terminal:

{% highlight shell%}
docker info
{% endhighlight %}

The host's characteristics considered for the experiment replication are the
number of CPUs and amount of main memory. The command's output shows such values
according to the following picture.

![Hosts resources](/assets/hostResources.png)

**Note 1:** in case the host machine contains a hyper-thread processor, you
can consider the number of available CPUs as the double of the value shown by
the `docker info` command's output.

**Note 2:** the `Total Memory` shown must not be entirely used by the experiment
container, so it does not imposes much pagination during the analysis execution.

[Table 1](#Table1) shows the environment characteristics where our experiment
was executed and it comprises both host machine and container's characteristics.

<a name="Table1"></a>

|                         |      Host machine         |Docker container|
|:------------------------|:-------------------------:|:--------------:|
|**CPU model**            |Intel i5-4570TE, 2.70 Ghz  |       ---      |
|**\#CPU's cores**        |  4 (hyperthreaded) cores  |     4 cores    |
|**OS**                   |  64-bit CentOs Linux 7    |Ubuntu 16.04 LTS|
|**Main memory (Gb)**     |           8 Gb            |      6 Gb      |

_**Table 1:** specifications of host machine and the experiment container._


Our experiment environment used 100% of available CPUs and 75% of the main
memory. Such values must be taken into account when replicating the experiment,
so the replication container resembles our experiment environment as much as
possible. To create the container from an docker image and define how it uses
the host's resources you should execute the following instruction at a terminal
replacing the values between **[** and **]** by the appropriate values.

{% highlight shell%}
docker run -dt 
           --cpuset-cpus [min-max] 
           --memory [amount unit] 
           --name [name] 
           [image:tag] 
           /bin/bash
{% endhighlight%}

*Example:* for creating a docker container named `scalabilityAnalysis` similar
to the described by [Table 1](#Table1), the instruction for creating it would
be:

{% highlight shell%}
docker run -dt 
           --cpuset-cpus 0-3 
           --memory 6Gb 
           --name scalabilityAnalysis 
           reana-spl:istSubmission 
           /bin/bash
{% endhighlight %}

{:start="3"}
3. **Running the evaluation script:**

Once the experiment container had been created from docker image, the next step
is to execute the script that triggers the reliability analysis of the software
product lines. To access the containers's terminal, execute the following
instruction from host's terminal, replacing `[name]` by the container's name you
provided the previous step:

{% highlight shell %}
docker exec -ti [name] /bin/bash
{% endhighlight %} 

_Example:_ considering the previous example, the command line for accessing the
created container would be: 

{% highlight shell %}
docker exec -ti scalabilityAnalysis /bin/bash
{% endhighlight %}

The file `run-analysis.sh` (inside the experiment's folder `/reana-evaluation`
the root folder) contains the experiment script for performing the analysis of
software product lines.  Such script may receive a value for the `--times`
parameter to define how many times each analysis strategy will be executed for
each evolution of each software product line. In absence of this parameter the
evaluation script assumes 10 as default number for iterations. The instructions
for accessing and starting the evaluation script are shown below. 

{% highlight console %}
root@90c8d1e0e689:/# cd reana-evaluation/
root@90c8d1e0e689:/reana-evaluation# ./run_analysis.sh 
{% endhighlight %}

**Note 3:** the container will always start a `root` session.  
**Note 4:** each created container will receive an `id` (in the example above
the container's id is `90c8d1e0e689`). Such value will be different for the
container that you will create. 

The script will execute all analysis performed for the software product lines
and their evolutions presented at the paper. As it may take a long time to
finish it is recommended choosing a reasonable number of iterations for the
execution of the strategy analysis. In order to execute the statical analysis,
the number of iterations can not be less than 8. 

{:start="4"}
4. **Getting the analysis results**

As soon as the evaluations of all software product lines finish the statistical
analysis takes place for summarizing the analysis' results, applying the
suitable statistical tests and outputs its results by graphs and a report. Such
resuts are grouped by software product lines and show how each analysis strategy
demands time and space as the software product line evolves. All results of
statistical analysis are packaged at the file `results.tar.bz` inside the
`reana-evaluation` folder. 

In order to view its content it is necessary copy `results.tar.bz` file to the
host machine and extract its content. The file transfer from the experiment
container to the host machine is accomplished by the instruction shown below. In
a host's terminal type the following instruction, replacing `[name]` by the
container name: 

{% highlight shell %}
docker cp [name]:/reana-evaluation/results.tar.bz .
{% endhighlight %}

_Example_: considering out container example, the command line for copying the
results to the host machine would be:
{% highlight shell%}
docker cp scalabilityAnalysis:/reana-evaluation/results.tar.bz
{% endhighlight %}

After the file transfer finishes, the file `results.tar.bz` will be available at
your working directory. With the extracting tool of your preference, you must
open and extract the file. The results will for each software product line will
be available in its own folder. 

---

## Linux image




[docker]:            https://docker.com/
[docker-download]:   https://www.docker.com/products/docker
[reana-docker-repo]: https://hub.docker.com/r/splmc/reana-spl/
