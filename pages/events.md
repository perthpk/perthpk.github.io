---
layout: page
title: Events
permalink: /events
hero-image: /images/parkour/grant_instruct.jpg
hero-text: WHATS ON
---

To register for a Saturday class please buy a ticket from [Eventbrite](https://www.eventbrite.com.au/o/perth-parkour-inc-8630642536)

{% raw %}
<div>
<div id="events">
<i v-if="!events">Loading events from Eventbrite ...</i>
<div v-cloak v-for="event in events" class="callout success">
  <h4><a v-bind:href="event.url" target="_blank" v-html="event.name.html"></a></h4>
  <div v-html="event.description.html"></div>
</div>
<h4 v-cloak v-if="events == 0">There are no current classes scheduled - the last 3 classes are below.</h4>
<div v-cloak v-for="event in endedEvents" class="callout secondary">
  <h5><a v-bind:href="event.url" target="_blank" v-html="event.name.html"></a></h5>
  <div v-html="event.description.html"></div>
</div>
</div>
<script>
document.onreadystatechange = function () {
    if (document.readyState == 'complete') {
        $.get("https://www.eventbriteapi.com/v3/users/me/owned_events/?token=3HTPZLQ7T4LOE2DJQAIY&format=json&status=live", function(data) {
            window.app = new Vue({
                el: '#events',
                data: {
                    message: 'Hello Vue!',
                    events: data.events
                }
            });
        })
    }
};
</script>
</div>
{% endraw %}
