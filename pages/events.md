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
<div v-cloak id="events">
<div v-for="event in activeEvents" class="callout success">
  <h4><a v-bind:href="event.url" target="_blank" v-html="event.name.html"></a></h4>
  <div v-html="event.description.html"></div>
</div>
<h4 v-if="activeEvents == 0">There are no current classes scheduled - the last 3 classes are below.</h4>
<div v-for="event in endedEvents" class="callout secondary">
  <h5><a v-bind:href="event.url" target="_blank" v-html="event.name.html"></a></h5>
  <div v-html="event.description.html"></div>
</div>
</div>
<script>
document.onreadystatechange = function () {
    if (document.readyState == 'complete') {
        $.get("https://zpnv41w9qb.execute-api.ap-southeast-2.amazonaws.com/prod/ppkevents", function(data) {
            window.app = new Vue({
                el: '#events',
                data: {
                    message: 'Hello Vue!',
                    events: data.events.reverse().slice(0,3)
                },
                computed: {
                    activeEvents: function() {
                        return this.events.filter(function(event) {
                            return event.status == 'active';
                        });
                    },
                    endedEvents: function() {
                        return this.events.filter(function(event) {
                            return event.status == 'ended';
                        });
                    }
                }
            });
        })
    }
};
</script>
</div>
{% endraw %}