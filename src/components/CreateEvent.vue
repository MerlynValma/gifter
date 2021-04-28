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
      <textarea class="form-control" placeholder="New random ID will show here...">{{newUuid}}</textarea>
      <br>

      CURRENT INSTANCE UUID: <h6 class="uuid">{{ cuurentUuid }}</h6>
      STATIC UUID: <h6 class="uuid">{{ uuidSaved }}</h6>
      <br>
    </div>
  </div>
</template>


<script>
import UUID from "pure-uuid";
let uuid = new UUID (1);

export default {
  data () {
    return {
     cuurentUuid: uuid,
      newUuid: "",
      uuidSaved: "9be9a5a0-a821-11eb-96b8-f7acec5da4bc"
    };
  },

  methods: {
    generateUuid(){
      this.newUuid = uuid;
    }
  }
}
</script>