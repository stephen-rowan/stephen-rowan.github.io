---
title: "Meetings"
permalink: /meetings/
---


<h1>Meeting Summaries</h1>

{% assign json_data = site.data.meeting-summaries-by-id %}

{% for key, summaries in json_data %}
  <h2>Meeting ID: {{ key }}</h2>
  {% for summary in summaries %}
    <h3>{{ summary.meetingInfo.name }} - {{ summary.meetingInfo.date }}</h3>
    <p><strong>Host:</strong> {{ summary.meetingInfo.host }}</p>
    <p><strong>Documenter:</strong> {{ summary.meetingInfo.documenter }}</p>
    <p><strong>People Present:</strong> {{ summary.meetingInfo.peoplePresent }}</p>
    <p><strong>Purpose:</strong> {{ summary.meetingInfo.purpose }}</p>
    <h4>Working Documents:</h4>
    <ul>
      {% for doc in summary.meetingInfo.workingDocs %}
        <li><a href="{{ doc.link }}">{{ doc.title }}</a></li>
      {% endfor %}
    </ul>
    <h4>Agenda Items:</h4>
    <ul>
      {% for item in summary.agendaItems %}
        <li>{{ item.narrative }}</li>
      {% endfor %}
    </ul>
  {% endfor %}
{% endfor %}
