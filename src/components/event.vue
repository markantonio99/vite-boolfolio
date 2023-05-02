<template>
  <div>
    <p v-for="event in events" :key="event.id">{{ event.title }}</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      events: []
    }
  },
  methods: {
    fetchEvents() {
      axios.get('http://127.0.0.1:8000/api/events')
        .then(res => {
          const events = res.data.results; // Accedi alla proprietà 'events'
          this.events = events;
        })
        .catch(err => {
          console.log(err)
        })
    }
  },
  mounted() {
    this.fetchEvents()
  }
}
</script>

<style>
</style>
