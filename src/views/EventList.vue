<template>
  <div>
    <h1>Eventi</h1>
    <BaseIcon />
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'

export default {
  props: ['id'],
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    }
  },
  created() {
    EventService.getEvents()
      .then(response => {
        console.log(response)
        this.events = response.data
      })
      .catch(error => {
        console.log('There was an error: ' + error.response.data)
      })
  }
}
</script>
