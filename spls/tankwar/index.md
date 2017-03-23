---
layout:    default
title:     TankWar System
---
# TankWar feature model

## Original feature and behavioral models

![tankwar feature model][fmTankWar]

144 features.  
4.21\*10E18 products.

Click [here][cnfTankWar] to download the feature model in conjunctive normal form (CNF).
Click [here][bhvTankWar] to download the behavioral model.

---

## Evolutions of feature and behavioral models of BSN-SPL.

|:-:|:-:|:-:|
|**Evol.**|**Feature<br>model**|**Behavioral<br>models**|


{% for ev in site.data.tankwarEvolutionsData %}
| {{ev.evolution}} | <a href="{{ev.fmImage}}">(PNG)</a> <a href="{{ev.cnfFile}}">(CNF)</a> <a href="{{ev.xmlFmFile}}">(XML)</a> | <a href="{{ev.behavioralFile}}">(XML)</a>
{% endfor %}
---
_Last update: March 23th., 2017._


[fmTankWar]:  ../../assets/fmTankWar.png
[cnfTankWar]: CNF_tankwar.txt
[bhvTankWar]: uml_tankwar.tar.gz 










<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-91211747-1', 'auto');
  ga('send', 'pageview');

</script>

