<template>
  <div>
    <h1>Events Listing</h1>
    <EventCard
      v-for="event in events"
      :key="event.id"
      :event="event"
    ></EventCard>
    <p></p>
  </div>
</template>

<script>
import EventService from '../services/EventService'
import EventCard from '../components/Eventcard'

export default {
  components: {
    EventCard
  },
  created() {
    EventService.getEvents('/events')
      .then(response => {
        this.events = response.data
      })
      .catch(error => {
        console.log('There was an error:', error)
      })
  },
  data() {
    return {
      events: []
    }
  }
}
</script>
