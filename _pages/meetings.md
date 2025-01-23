---
title: "Meetings"
permalink: /meetings/
---

<h1>Workgroups</h1>

{% assign workgroups = site.data.workgroups %}

{% for group in workgroups %}
  <h2>{{ group.workgroup }}</h2>
  <p><strong>Workgroup ID:</strong> {{ group.workgroup_id }}</p>
  
<h3>Meeting Information</h3>
  <ul>
    <li><strong>Name:</strong> {{ group.meetingInfo.name }}</li>
    <li><strong>Date:</strong> {{ group.meetingInfo.date }}</li>
    <li><strong>Host:</strong> {{ group.meetingInfo.host }}</li>
    <li><strong>Documenter:</strong> {{ group.meetingInfo.documenter }}</li>
    <li><strong>People Present:</strong> {{ group.meetingInfo.peoplePresent }}</li>
    <li><strong>Purpose:</strong> {{ group.meetingInfo.purpose }}</li>
    <li><strong>Working Docs:</strong>
      <ul>
        {% for doc in group.meetingInfo.workingDocs %}
          <li><a href="{{ doc.link }}">{{ doc.title }}</a></li>
        {% endfor %}
      </ul>
    </li>
  </ul>

  <h3>Tags</h3>
  <ul>
    <li><strong>Topics Covered:</strong> {{ group.tags.topicsCovered }}</li>
    <li><strong>Emotions:</strong> {{ group.tags.emotions }}</li>
  </ul>
{% endfor %}


