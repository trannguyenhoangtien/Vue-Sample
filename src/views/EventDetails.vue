<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  props: ['id'],

  created() {
    //fetch event (by id) and set local data
    this.$store.dispatch('event/fetchEvent', this.id)
    //this.fetchEvent(this.id)
  },
  computed: {
    ...mapState({
      event: (state) => state.event.event,
    }),
  },
  //methods: mapActions('event', ['fetchEvent']),
}
</script>