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
    a test {{ message }}
</div>
<script>
document.onreadystatechange = function () {
    if (document.readyState == 'complete') {
        $.get("https://zpnv41w9qb.execute-api.ap-southeast-2.amazonaws.com/prod/ppkevents", function(data) {
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