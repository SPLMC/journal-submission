---
layout:    default
title:     Lift System
---
# Lift feature model

## Original feature and behavioral models

![lift feature model][fmLift]

10 features.  
512 products.

Click [here][cnfLift] to download the feature model in conjunctive normal form (CNF).
Click [here][bhvLift] to download the behavioral model.

---

## Evolutions of feature and behavioral models of Lift system.

|:-:|:-:|:-:|
|**Evol.**|**Feature<br>model**|**Behavioral<br>models**|


{% for ev in site.data.liftEvolutionsData %}
| {{ev.evolution}} | <a href="{{ev.fmImage}}">(PNG)</a> <a href="{{ev.cnfFile}}">(CNF)</a> <a href="{{ev.xmlFmFile}}">(XML)</a> | <a href="{{ev.behavioralFile}}">(XML)</a>
{% endfor %}
---
_Last update: March 21th., 2017._


[fmLift]:  ../../assets/fmLift.png
[cnfLift]: CNF_lift.txt
[bhvLift]: uml_lift.tar.gz










<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-91211747-1', 'auto');
  ga('send', 'pageview');

</script>

