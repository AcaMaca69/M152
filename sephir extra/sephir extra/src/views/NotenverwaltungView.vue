<template>
  <div class="container">
    <div class="content" v-for="(noten, fach) in Fächer" :key="fach">
      <div class="faecher">{{ fach }} <a>Ø: {{ parseFloat(calculateAverageGrade(fach)).toFixed(2) }}</a></div>
      <br>
      <div class="notezeigen" v-for="(note, index) in noten.noten" :key="index">
        <div>
          {{ parseFloat(note).toFixed(2) }}
          <button @click="deleteNote(fach, index)">&#10008;</button>
        </div>
        <br>          
      </div>
      <br>
      <div class="Add"><input type="number" min="0" max="6" @keyup.enter="addNote($event, fach)" /></div>
      <br>
      <br>
    </div>
  </div>
</template>

<script setup>
import { ref } from "@vue/reactivity";

const Fächer = ref({
  SPO: { noten: [3.5, 5] },
  M306: { noten: [2, 1, 3] },
  M152: { noten: [2, 5] },
  M153: { noten: [5] },
  WUR: { noten: [2, 3] },
  NWS: { noten: [5, 1] },
  SPK: { noten: [3.2] },
  GES: { noten: [5.2] },
  M151: { noten: [2.7] },
});

function deleteNote(fach, note) {
  Fächer.value[fach].noten.splice(note, 1);
}

function addNote(e, fach) {
  let newNote = Math.min(6, Math.max(1, parseInt(e.target.value)));
  Fächer.value[fach].noten.push(newNote);
}

function calculateAverageGrade(fach) {
  let sum = 0;
  for (let note of Fächer.value[fach].noten) {
    sum += note;
  }
  return sum / Fächer.value[fach].noten.length;
}
</script>
