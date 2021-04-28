<template>
  <div class="event">
    <h1>This is an EVENT page</h1>
    <br>
    <CreateEvent/>
  </div>

</template>

<script>
// @ is an alias to /src
import CreateEvent from '@/components/CreateEvent.vue'
export default {
  name: 'Event',
  components: {
    CreateEvent
  }
}
</script>

<style scoped>

</style>