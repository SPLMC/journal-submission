---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
---

# Suplementary material for *IST* submission:

## Description

Model Checking techniques have been applied to ensure software systems achieve desired quality levels and fulfill functional and non-functional requirements. However, employing these techniques to software product lines is a challenging task, given the exponential blowup of the number of products. Current product line model checking techniques leverage symbolic model checking and variability information to optimize the analysis, but still face limitations that make them costly or even unfeasible for some product lines. We present a feature-family-based strategy to efficiently analyze reliability of product lines. Our approach limits the effort needed to compute the reliability of a product line by dividing its behavioural models into smaller units, which can be model-checked more efficiently. It also computes the reliability for all configurations at once, by means of a suitable variational data structure. The results show our strategy significantly outperformed the others in terms of time and space.

## ReAna tool

ReAna is the tool implementing the feature-family-based strategy for the reliability analysis of software product lines. It can be downloaded from [here][reana-tool], and its source code is available at [https://github.com/SPLMC/reana/][reana-repo].

## ReAna variants

In our empirical study we compare the feature-family-based strategy with 4 other evaluation strategies: product-based, family-based, feature-product-based and family-product-based. A command-line configurable version of ReAna tool implementing all these strategies can be downloaded from [here][reana-spl-tool], and its source code is available at [https://github.com/SPLMC/reana-spl/][reana-spl-repo].

| Product lines |    Feature Model     |  Behavioral Models\*  | Results |
|---------------|:--------------------:|:---------------------:|:-------:|
| Email         | [click][fmemail]     | [click][bmemail]      | click   |
| MinePump      | [click][fmminepump]  | [click][bmminepump]   | click   |
| BSN           | [click][fmbsn]       | [click][bmbsn]        | click   |
| Lift          | [click][fmlift]      | [click][bmlift]       | click   |
| InterCloud    | [click][fmintercloud]| [click][bmintercloud] | click   |
| TankWar       | [click][fmtankwar]   | [click][bmtankwar]    | click   |

\* All behavioral models were created using the [MagicDraw][magicdraw] tool.



## Overall results  (already in the paper)

Overall, our experiments show that the feature-family-based strategy is faster, with statistical significance, than all other analysis strategies, as shown by the figure below. 

The feature-family-based strategy also demanded less memory than the others in most cases, as shown by the figure below. The only exceptions were family-based analysis of Email and Lift systems, with feature-family-based strategy consuming near 5% and 4% more memory, respectively (but faster). 


## Experiment replication

Click here for additional information for replicating our experiment.

## [Contacts](site/contacts)


[reana-tool]:     https://github.com/reana/fse16/raw/master/reana/reana.jar
[reana-repo]:     https://github.com/SPLMC/reana/
[reana-spl-tool]: https://github.com/reana/fse16/raw/master/reana-spl/reana-spl.jar
[reana-spl-repo]: https://github.com/SPLMC/reana-spl/
[magicdraw]:      http://www.nomagic.com/products/magicdraw.html
[fmemail]:        spls/email/
[bmemail]:        spls/email/uml_email.xml
[fmminepump]:     spls/minepump/
[bmminepump]:     spls/minepump/uml_minepump.xml
[fmbsn]:          spls/bsn/
[bmbsn]:          spls/bsn/uml_bsn.xml
[fmlift]:         spls/lift/
[bmlift]:         spls/lift/uml_lift.xml
[fmintercloud]:   spls/intercloud/
[bmintercloud]:   spls/intercloud/uml_intercloud.xml
[fmtankwar]:      spls/tankwar/
[bmtankwar]:      spls/tankwar/uml_tankwar.xml
