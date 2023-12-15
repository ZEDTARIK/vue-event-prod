<script>
import EventService from "@/service/EventService";
export default {
  name: "EventDetail",
  props: ['id'],
  data: function() {
    return {
      event: null
    }
},
  created() {
    EventService.getEventById(this.id)
        .then((rsp) => {
          this.event = rsp.data
        })
        .catch(err => console.error(err))
  }
}
</script>

<template class="row" >
  <div class="col-md-8 mx-auto" v-if="event">

    <div class="toast show" role="alert" aria-live="assertive" aria-atomic="true">
      <div class="toast-header">
        <strong class="me-auto">{{ event.title }}</strong>
        <small> {{ event.time }} ago</small>
      </div>
      <div class="toast-body">
        {{ event.description }}
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>