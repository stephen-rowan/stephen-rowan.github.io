---
title: "Meetings"
permalink: /meetings/
---
<h1>Workgroup Information</h1>

---
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

<h3>Agenda Items</h3>
  {% for item in group.agendaItems %}
    
    <h4>Status: {{ item.status }}</h4>
    <p>{{ item.narrative | newline_to_br }}</p>

  <h5>Action Items</h5>
    <ul>
      {% for action in item.actionItems %}
        <li>
          <strong>Status:</strong> {{ action.status }} <br>
          <strong>Text:</strong> {{ action.text }} <br>
          <strong>Assignee:</strong> {{ action.assignee }} <br>
          <strong>Due Date:</strong> {{ action.dueDate }}
        </li>
      {% endfor %}
    </ul>

  <h5>Decision Items</h5>
    <ul>
      {% for decision in item.decisionItems %}
        <li>
          <strong>Decision:</strong> {{ decision.decision }} <br>
          <strong>Rationale:</strong> {{ decision.rationale }} <br>
          <strong>Effect:</strong> {{ decision.effect }}
        </li>
      {% endfor %}
    </ul>

  <h5>Discussion Points</h5>
    <ul>
      {% for point in item.discussionPoints %}
        <li>{{ point }}</li>
      {% endfor %}
    </ul>
  {% endfor %}

  <h3>Tags</h3>
  <ul>
    <li><strong>Topics Covered:</strong> {{ group.tags.topicsCovered }}</li>
    <li><strong>Emotions:</strong> {{ group.tags.emotions }}</li>
  </ul>
{% endfor %}
