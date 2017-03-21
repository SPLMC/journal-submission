---
layout:    default
title:     Intercloud System
---
# Intercloud feature model

## Original feature and behavioral models

![intercloud feature model][fmIntercloud]

54 features.  
110592 products.

Click [here][cnfIntercloud] to download the feature model in conjunctive normal form (CNF).
Click [here][bhvIntercloud] to download the behavioral model.

---

## Evolutions of feature and behavioral models of Intercloud.

|:-:|:-:|:-:|
|**Evol.**|**Feature<br>model**|**Behavioral<br>models**|


{% for ev in site.data.intercloudEvolutionsData %}
| {{ev.evolution}} | <a href="{{ev.fmImage}}">(PNG)</a> <a href="{{ev.cnfFile}}">(CNF)</a> <a href="{{ev.xmlFmFile}}">(XML)</a> | <a href="{{ev.behavioralFile}}">(XML)</a>
{% endfor %}
---
_Last update: March 21th., 2017._


[fmIntercloud]:  ../../assets/fmInterCloud.png
[cnfIntercloud]: CNF_intercloud.txt
[bhvIntercloud]: uml_intercloud.tar.gz









<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-91211747-1', 'auto');
  ga('send', 'pageview');

</script>

