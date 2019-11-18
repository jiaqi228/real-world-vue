<template>
  <div>
    <h1>Event Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <BaseIcon />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'
export default {
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    }
  },
  /*eslint no-console: ["error", { allow: ["warn", "error"] }] */
  created() {
    EventService.getEvents()
      .then(reponse => {
        this.events = reponse.data
      })
      .catch(error => {
        console.error('There was an error:' + error.reponse)
      })
  }
}
</script>
