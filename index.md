---
layout: page
title: Home
permalink: /
hero-image: /images/2016finalclass/poserclimbup.jpg
hero-style: "height: 65vh;"
hero-text:
---

### Upcoming events

Find your passion for Parkour by joining in classes, workshops and other training sessions with the Perth Parkour community. To register for a Saturday class please buy a ticket from [Eventbrite](https://www.eventbrite.com.au/o/perth-parkour-inc-8630642536).

{% raw %}
<div>
<div id="events">
<p v-if="!events" class="text-center"><i>Loading events from Eventbrite ...</i></p>
<div class="callout" v-cloak v-for="event in events">
  <h4 v-html="event.name.html"></h4>
  <a class="button" v-bind:href="event.url" target="_blank">Book online with Eventbrite</a>
  <div v-html="event.description.html"></div>
</div>
<h4 v-cloak v-if="events == 0">There are no current classes scheduled =(</h4>
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

### Get in touch

Before <a href="/contact">contacting us</a>, please note the following:

 - Our regular Saturday classes are available to everyone regardless of age, gender or fitness level
 - Our classes run in rain, hail or shine
 - For your first class please pre-fill a [waiver](http://www.parkour.asn.au/docs/APA_waiver.pdf) and bring it with you

