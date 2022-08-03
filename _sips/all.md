---
layout: sips
title: List of All SIPs

redirect_from: 
  - "/sips/sip-list.html"
  - "/sips/pending/index.html"
---

{% assign sips = site.sips | sort: title %}
{% assign sipData = site.data.sip-data %}

## Pre-SIP Discussions

You can find so-called “pre-SIP discussions” in the Scala Contributors forum, under
the category [Scala Improvement Process](https://contributors.scala-lang.org/c/sip/13).
The goal of pre-SIP discussions is to gather initial community feedback and support.

## Pending SIPs

Proposals that are at the design or implementation stage, and that are actively
discussed by the committee and the proposals’ authors. Click on a proposal to
read its content, or the corresponding discussions on GitHub if its design has
not been accepted yet.

<div class="sip-list">
  <ul>
  {% for sip in sips %}
   {% if sip.stage == "design" or sip.stage == "implementation" %}
     <li class="no-fragmentation">
      <strong>
        <a href="{% if sip.pull-request-number %}https://github.com/scala/improvement-proposals/pull/{{ sip.pull-request-number }}{% else %}{{ sip.url }}{% endif %}">
          {{ sip.title }}
        </a>
      </strong>
      <div class="tag" style="background-color: {{ sipData[sip.stage].color }}">Stage: {{ sipData[sip.stage].text }}</div>
      <div class="tag" style="background-color: {{ sipData[sip.status].color }}">Status: {{ sipData[sip.status].text }}</div>
      {% if sip.recommendation %}
        <div class="tag" style="background-color: {{ sipData[sip.recommendation].color }}">Recommendation: {{ sipData[sip.recommendation].text }}</div>
      {% endif %}
     </li>
   {% endif %}
  {% endfor %}
  </ul>
</div>

## Completed SIPs

Proposals that have been implemented in the compiler and that are available as a stable
feature of the compiler (shipped), or that will be available in the next minor release
of the compiler (accepted). Click on a proposal to read its content.

<div class="sip-list">
  <ul>
  {% for sip in sips %}
   {% if sip.stage == "completed" %}
     <li class="no-fragmentation">
      <strong><a href="{{ sip.url }}">{{ sip.title }}</a></strong>
      <div class="tag" style="background-color: {{ sipData[sip.status].color }}">{{ sipData[sip.status].text }}</div>
     </li>
   {% endif %}
  {% endfor %}    
  </ul>
</div>

## Rejected SIPs

Proposals that have been rejected by the committee. Click on a proposal to read the
corresponding discussions on GitHub.

<div class="sip-list">
  <ul>
  {% for sip in sips %}
   {% if sip.status == "rejected" %}
     <li>
      <strong><a href="https://github.com/scala/improvement-proposals/pull/{{ sip.pull-request-number }}">{{ sip.title }}</a></strong>
     </li>
   {% endif %}
  {% endfor %}    
  </ul>    
</div>

## Withdrawn SIPs

Proposals that have been withdrawn by their authors. Click on a proposal to read the 
corresponding discussions on GitHub.

<div class="sip-list">
  <ul>
  {% for sip in sips %}
   {% if sip.status == "withdrawn" %}
     <li>
      <strong><a href="https://github.com/scala/improvement-proposals/pull/{{ sip.pull-request-number }}">{{ sip.title }}</a></strong>
     </li>
   {% endif %}
  {% endfor %}
  </ul>
</div>
