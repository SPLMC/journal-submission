---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
---

# Suplementary material for *<<journal's name>>* submission:

## Description

Model Checking techniques have been applied to ensure software systems achieve
desired quality levels and fulfill functional and non-functional requirements.
However, employing these techniques to software product lines is a challenging
task, given the exponential blowup of the number of products. Current product
line model checking techniques leverage symbolic model checking and variability
information to optimize the analysis, but still face limitations that make them
costly or even unfeasible for some product lines. We present a
feature-family-based strategy to efficiently analyze the reliability of product
lines. Our approach limits the effort needed to compute the reliability of a
product line by dividing its behavioural models into smaller units, which can be
model-checked more efficiently. It also computes the reliability for all
configurations at once, by means of a suitable variational data structure. The
results show our strategy significantly outperformed the others in terms of time
and space.

## ReAna tool

ReAna is the tool implementing the feature-family-based strategy for the
reliability analysis of software product lines. It can be downloaded from
[here][reana-tool], and its source code is available at
[https://github.com/SPLMC/reana/][reana-repo].

## ReAna variants

In our empirical study we compare the feature-family-based strategy with 4 other
evaluation strategies: product-based, family-based, feature-product-based and
family-product-based. A command-line configurable version of ReAna tool
implementing all these strategies can be downloaded from [here][reana-spl-tool],
and its source code is available at
[https://github.com/SPLMC/reana-spl/][reana-spl-repo].

## Empirical evaluation of ReAna variants

To compare the evaluations strategies implemented by ReAna-SPL, an empirical
study was performed to analyze 6 different software product lines, namely: EMail
System, Minepump, BSN-SPL, Lift System, Intercloud and Tankwar.  Such systems
comprises different domains like communication, control systems, cloud
deployment and games and their configuration spaces range from from dozen to
billions of products. The feature and behavioral models of each subject system
are available at the second and third column of the following table.

| Product lines |    Feature Model     |  Behavioral Models\*  | Results               |
|---------------|:--------------------:|:---------------------:|:---------------------:|
| Email         | [click][fmemail]     | [click][bmemail]      | [click][rsemail]      |
| MinePump      | [click][fmminepump]  | [click][bmminepump]   | [click][rsminepump]   |
| BSN           | [click][fmbsn]       | [click][bmbsn]        | [click][rsbsn]        |
| Lift          | [click][fmlift]      | [click][bmlift]       | [click][rslift]       |
| InterCloud    | [click][fmintercloud]| [click][bmintercloud] | [click][rsintercloud] |
| TankWar       | [click][fmtankwar]   | [click][bmtankwar]    | [click][rstankwar]    |

\* All behavioral models were created using the [MagicDraw][magicdraw] tool.

To notice how each evaluation strategy behaves as the software product line
under analysis increases, the experimental study augmented the subject system's
complexity by adding an optional feature and its respective behavior (described
by a sequence diagram fragment). The results in time and space for each subject
system (and it evolutions) are available at the 'Results' column of the the
table above.

## Overall results  (already in the paper)

Overall, the experiment shows the feature-family-based strategy is faster, with
statistical significance, than all other analysis strategies as shown by results
provided for each subject system. 

The empirical evaluation shows the feature-family-based strategy significantly
outperformed state-of-the-art strategies in terms of time and space, being the
only one that could be scaled to a 2^20 increase in the configuration space

The explanation why feature-family-based strategy performs better than others is
threefold. The first reason is due the fact the feature-family-based strategy
limits the effort needed to compute the reliability of a product line by
dividing its behavioral models into smaller units, which can be model-checked
more efficiently.  The second reason deccurs from the reuse of reliability
computation for redundant behaviors as the strategy performs this reliability
computation for all configurations at once by evaluating reliability expressions
in terms of ADDs. Finally, the use of decision diagrams for encoding presence
conditions and the rules from the feature model restricts that computation of
reliability values only for valid configurations, i.e., no effort is dispended
for computing reliability values of ill-formed products.


## Experiment replication

Click [here](replication.html) for additional information for replicating our
experiment.

## [Contacts](site/contacts)


[reana-tool]:     https://github.com/reana/fse16/raw/master/reana/reana.jar
[reana-repo]:     https://github.com/SPLMC/reana/
[reana-spl-tool]: https://github.com/reana/fse16/raw/master/reana-spl/reana-spl.jar
[reana-spl-repo]: https://github.com/SPLMC/reana-spl/
[magicdraw]:      http://www.nomagic.com/products/magicdraw.html
[fmemail]:        spls/email/
[bmemail]:        spls/email/uml_email.tar.gz
[fmminepump]:     spls/minepump/
[bmminepump]:     spls/minepump/uml_minepump.tar.gz
[fmbsn]:          spls/bsn/
[bmbsn]:          spls/bsn/uml_bsn.tar.gz
[fmlift]:         spls/lift/
[bmlift]:         spls/lift/uml_lift.tar.gz
[fmintercloud]:   spls/intercloud/
[bmintercloud]:   spls/intercloud/uml_intercloud.tar.gz
[fmtankwar]:      spls/tankwar/
[bmtankwar]:      spls/tankwar/uml_tankwar.tar.gz
[rsbsn]:          spls/bsn/resultsBSN.html
[rsemail]:        spls/email/resultsEmail.html
[rsminepump]:     spls/minepump/resultsMinepump.html
[rslift]:         spls/lift/resultsLift.html
[rsintercloud]:   spls/intercloud/resultsIntercloud.html
[rstankwar]:      spls/tankwar/resultsTankwar.html
