<template>
   <div class="note">
        <div v-if="note">
            <h3>Gift</h3>
            <div class="form-group">
                <input class="form-control" type="text" v-model="note.title" placeholder="Your Name" />
            </div>
            <div class="form-group">
                <textarea class="form-control" v-model="note.content" placeholder="Your Gift"></textarea>
            </div>
            <button class="btn btn-danger" @click="removeNote()">Remove from DB</button>
            <button class="btn btn-success" @click="saveNote()">Save to DB</button>
        </div>
        <div v-else>
            <h5>Please create new Note...</h5>
        </div>
        
    </div> 
</template>

<script>
export default {
  name: "Note",
  props: ["note"],
  methods: {
    saveNote() {
      this.$emit("app-saveNote");
    },
    removeNote() {
      this.$emit("app-removeNote");
    }
  }
};
</script>

<style>
.note {
  margin: 20px;
}
</style>