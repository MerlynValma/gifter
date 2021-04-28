<template>
  <div class="event">
    <br>
    <div style="color: black;">
      <h5>Creating unique ID for each event, your event ID is:</h5>
      <br>
      On "+Create Event" generate new UUID. Use generated UUID for new instance event.
      <br>
      <button class="btn btn-success" @click="generateUuid()">+ Create Event</button>
      <br>
      <textarea class="form-control" v-model="id" placeholder="Your ID will show here...">{{newUuid}}</textarea>
      <br>

      CURRENT INSTANCE UUID: <h6 class="uuid">{{ uuid }}</h6>
      STATIC UUID: <h6 class="uuid">{{ uuidSaved }}</h6>
      <br>
    </div>
  </div>

</template>

<script>
import { uuid } from 'vue-uuid'; // uuid object is also exported to things
// outside Vue instance.

const NAMESPACE = "65f9af5d-f23f-4065-ac85-da725569fdcd";

export default {
  data () {

    return {
      NAMESPACE,
      uuid: uuid.v1(),
      uuidSaved: this.$uuid.v5("instanceID", NAMESPACE),
      newUuid: ""
    };
  },

  methods: {
    generateUuid(){
      this.newUuid = uuid.v4();
    }
  }

}
</script>

<style scoped>

</style>