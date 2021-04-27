<template>
  <div id="app">

    <app-header/>

    <router-view/>


    <div style="color: orangered;">
      <h1>Gifterrrrr</h1>
    </div>
    <div style="color: black;">
      <h5>Never have 3 toasters for your wedding. <br>Never again get 5 books for your birthday.</h5>
      <h9>Event planners can create a new event (birthday, wedding etc.) and let participants know, what they would like
        to receive.
      </h9>
    </div>
    <div class="row">
      <div class="col-sm-4">
        <NotesList
            @app-addNote="addNote"
            @app-changeNote="changeNote"
            :notes="notes"
            :activeNote="index"/>
      </div>
      <div class="col-sm-6">
        <Note
            @app-saveNote="saveNote"
            @app-removeNote="removeNote"
            :note="notes[index]"/>
      </div>
    </div>

    <app-footer/>

  </div>
</template>

<!-- The core Firebase JS SDK is always required and must be listed first -->

<script src="/__/firebase/8.4.2/firebase-analytics.js"></script>
<script src="/__/firebase/8.4.1/firebase-database.js"></script>
<!-- Initialize Firebase -->
<script src="/__/firebase/init.js"></script>


<script>
import GiftList from "@/components/GiftList.vue";
import Note from "@/components/Gift.vue";
import AppHeader from "@/components/AppHeader.vue";
import AppFooter from "@/components/AppFooter.vue";
import firebase from "firebase/app";
import "firebase/database";

var config = {
  apiKey: "AIzaSyBUTZaBzkB2dzxjdhloU6-evE7a6msYivI",
  authDomain: "gifter-b50fc.firebaseapp.com",
  databaseURL: "https://gifter-b50fc-default-rtdb.firebaseio.com",
  projectId: "gifter-b50fc",
  storageBucket: "gifter-b50fc.appspot.com",
  messagingSenderId: "17931634028",
  appId: "1:17931634028:web:5b101f77b63093cb525f49",
  measurementId: "G-GY089HBTM0"
};
firebase.initializeApp(config);
const database = firebase.database();
const notesRef = database.ref("notes");

export default {
  name: "app",
  components: {
    NotesList: GiftList,
    Note,
    AppHeader,
    AppFooter
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

    saveNote() {
      const note = this.notes[this.index];
      if (note.id) {
        this.updateNote(note);
      } else {
        this.createNote(note);
      }
    },


    updateNote(note) {
      notesRef.child(note.id).update({
        title: note.title,
        content: note.content
      });
    },


    createNote(note) {
      note.id = notesRef.push(note).key;
    },


    removeNote() {
      const id = this.notes[this.index].id;
      notesRef.child(id).remove();
    }
  },


  created() {
    notesRef.once("value", notes => {
      notes.forEach(note => {
        this.notes.push({
          id: note.ref.key,
          title: note.child("title").val(),
          content: note.child("content").val()
        });
      });
    });

    /* eslint-disable no-console */
    // value = snapshot.val() | id = snapshot.key
    notesRef.on("child_added", snapshot => {
      console.log("note was added: ", {...snapshot.val(), id: snapshot.key});
    });

    notesRef.on("child_removed", snapshot => {
      const deletedNote = this.notes.find(note => note.id === snapshot.key);
      console.log("note was removed: ", deletedNote);

      const index = this.notes.indexOf(deletedNote);
      this.notes.splice(index, 1);
      this.index = this.index === 0 ? 0 : index - 1;
    });

    notesRef.on("child_changed", snapshot => {
      const updatedNote = this.notes.find(note => note.id === snapshot.key);
      updatedNote.title = snapshot.val().title;
      updatedNote.content = snapshot.val().content;
      console.log("note was updated: ", updatedNote);
    });
    /* eslint-enable no-console */
  }
};
</script>

<style>
#app {
  text-align: center;
  max-width: 1000px;
}
</style>