<template>
  <div id="app">
    <div style="color: orangered;">
      <h1>Gifter</h1>
    </div>
    <div style="color: black;">
      <h5>Never have 5 toasters for your wedding. <br>Never again worry about what to give...</h5>
      <h9>Event planners can create a new event (birthday, wedding etc.) and let participants know, what they would like
        to receive. </h9>
    </div>
    <div class="row">
      <div class="col-sm-6">
        <NotesList
            @app-addNote="addNote"
            @app-changeNote="changeNote"
            :notes="notes"
            :activeNote="index"/>
      </div>
      <div class="col-sm-6">
        <Note
            @app-removeNote="removeNote"
            :note="notes[index]"/>
      </div>
    </div>
  </div>
</template>

<script>
import NotesList from "./components/NotesList.vue";
import Note from "./components/Note.vue";

export default {
  name: "app",
  components: {
    NotesList,
    Note
  },
  data: () => ({
    notes: [],
    index: 0
  }),
  methods: {
    addNote() {
      this.notes.push({
        title: "",
        content: ""
      });
      this.index = this.notes.length - 1;
    },
    changeNote(index) {
      this.index = index;
    },
    removeNote() {
      this.notes.splice(this.index, 1);
      this.index = this.index === 0 ? 0 : this.index - 1;
    }
  }
};
</script>

<style>
#app {
  text-align: center;
  max-width: 700px;
}
</style>