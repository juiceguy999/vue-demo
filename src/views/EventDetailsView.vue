<script setup>

import {onMounted, ref, reactive} from "vue";
import EventService from "../../services/EventService.js";

const event = ref(null);
const props = defineProps({
  id: {
    required: true
  }
})

onMounted(() => {
  EventService.getEvent(props.id)
    .then((res) => event.value = res.data)
})
</script>

<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} at {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<style scoped>

</style>