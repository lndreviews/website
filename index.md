---
layout: default
title: home
---
### A weekly review club for LND PRs

<span class="question">What is this?</span> &nbsp;A weekly club for reviewing
LND PRs **every two weeks on Thursdays at 17:00 UTC** in the #lnd-pr-reviews IRC channel on [libera.chat](https://kiwiirc.com/nextclient/irc.libera.chat/).

<span class="question">What's it for?</span> &nbsp;To help newer contributors
learn about the LND review process. The review club is *not* primarily
intended to help open PRs get merged (although that might be a nice
side-effect).

<span class="question">Who should take part?</span> &nbsp;Anyone who wants to
learn about contributing to LND. All are welcome to come and ask
questions!

<span class="question">What's the benefit for participants?</span>
&nbsp;Reviewing and testing PRs is the best way to start contributing to LND,
but it's difficult to know where to start. There are hundreds of open PRs,
many require a lot of contextual knowledge, and contributors and reviewers often
use unfamiliar terminology. The review club will give you the tools and
knowledge you need in order to take part in the [LND review
process](https://github.com/lightningnetwork/lnd/blob/master/docs/code_contribution_guidelines.md#code-review)
on GitHub.

<span class="question">How do I take part?</span> Just show up on IRC! See
[Attending your first PR Review Club](https://github.com/lightningnetwork/lnd/blob/master/docs/code_contribution_guidelines.md#code-review) 
for more tips on how to participate.

<span class="question">Who runs this?</span> &nbsp;Lightning Labs evangelist
[lucasdcf](https://github.com/lucasdcf) started the review club and schedules
the upcoming meetings. Individual meetings are hosted by a variety of LND
contributors. See some of our [previous hosts](/meetings-hosts/).

## Upcoming Meetings


<table>
{% for post in site.posts reversed %}
  {% capture components %}
  {%- for comp in post.components -%}
    <a href="/meetings-components/#{{comp}}">{{comp}}</a>{% unless forloop.last %}, {% endunless %}
  {%- endfor -%}
  {% endcapture %}
  {% if post.status == "upcoming" %}
    <tr>
      <div class="home-posts-post">
        <td class="Home-posts-post-date">{{ post.date | date_to_string }}</td>
        <td class="Home-posts-post-arrow">&raquo;</td>
        <td><a class="Home-posts-post-title" href="{{ post.url }}">{% if post.pr %}#{{ post.pr }} {% endif %} {{ post.title }}</a>
        ({{components}})
        <span class="host">hosted by
        <a class="host" href="/meetings-hosts/#{{post.host}}">{{ post.host }}</a>
        </span></td>
      </div>
    </tr>
  {%- endif -%}
{% endfor %}
</table>

We're always looking for interesting PRs to discuss in the review club and for
volunteer hosts to lead the discussion:

- To suggest a PR, please DM @lucasdcf on [Slack](https://lightning.engineering/slack.html), IRC, or Twitter.
- If you'd like to host a meeting, look at the [information for meeting
  hosts](https://github.com/lndreviews/website/blob/master/CONTRIBUTING.md)
  and contact lucasdcf on on [Slack](https://lightning.engineering/slack.html), IRC, or Twitter.

## Recent Meetings

<table>
{% assign count = 0 %}
{% for post in site.posts %}
  {% capture components %}
  {%- for comp in post.components -%}
    <a href="/meetings-components/#{{comp}}">{{comp}}</a>{% unless forloop.last %}, {% endunless %}
  {%- endfor -%}
  {% endcapture %}
  {% if post.status == "past" %}
    {% assign count = count | plus: 1 %}
    <tr>
      <div class="home-posts-post">
        <td class="Home-posts-post-date">{{ post.date | date_to_string }}</td>
        <td class="Home-posts-post-arrow">&raquo;</td>
        <td><a class="Home-posts-post-title" href="{{ post.url }}">{% if post.pr %}#{{ post.pr }}{% endif %} {{ post.title }}</a>
        ({{components}})
        <span class="host">hosted by <a class="host" href="/meetings-hosts/#{{post.host}}">{{ post.host }}</a></span></td>
      </div>
    </tr>
  {%- endif -%}
  {% if count == 4 %}
    {% break %}
  {% endif %}
{% endfor %}
</table>

See all [meetings](/meetings/).

## Other Resources for New Contributors

- Read the [Contributing to LND
  Guide](https://github.com/lightningnetwork/lnd/blob/master/docs/code_contribution_guidelines.md). This
  will help you understand the process and some of the terminology we use in
  LND.
- Look at the [Good First
  Issues](https://github.com/lightningnetwork/lnd/labels/good%20first%20issue)
  and [Up For
  Grabs](https://github.com/lightningnetwork/lnd/labels/up%20for%20grabs)
  list.
