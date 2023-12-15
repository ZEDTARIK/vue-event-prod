<style scoped>
.router-link {
  color: #2c3e50;
  text-decoration: none;
}
.event {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
}

.event:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}
</style>
<script>
export default {
  name: "EventCard",
  props: {
    event: {
      type: Object,
      require: true
    },
  }
}
</script>

<template class="event">
  <router-link :to="{ name : 'EventDetail' , params: { id: event.id } }" class="router-link">
  <div class="card border-primary mb-3">
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
  </router-link>
</template>
