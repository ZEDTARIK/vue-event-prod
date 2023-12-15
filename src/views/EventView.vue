<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;

}
</style>
<template class="row mt-3">
  <div class="col-md-12">
    <h3> List Events</h3>
    <div class="events">
      <EventCard v-for="event in events"  :key="event.id" :event="event"/>
    </div>
  </div>

</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from "@/service/EventService";

export default {
  name: 'EventView',
  components: {
    EventCard
  },
  data: function(){
    return {
        events: null
    }
  },
  created() {
    EventService.getEvents()
        .then((response) => {
          this.events = response.data
        })
        .catch((error) => console.error(error))
  }
}
</script>
