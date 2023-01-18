<script setup lang="ts">
import {ref} from "vue";

const props = defineProps({
  text: {
    default: "",
  },
});

const text = ref(props.text);
const voices = window.speechSynthesis.getVoices();
const usableVoices = ["evan (enhanced)", "zoe (premium)", "tom (enhanced)"];

// console.log(voices);
function speakUtterance() {
  var msg = new SpeechSynthesisUtterance();
  var voices = window.speechSynthesis.getVoices();
  voices.forEach((voice) => {
    console.log(voice.name);
    if (voice.name.toLowerCase().includes("zoe (premium)")) {
      console.log(voice);
      msg.voice = voice;
    }
  });
  // msg.voice = voices[0];
  // console.log(voices);
  msg.volume = 1; // From 0 to 1
  msg.rate = 1; // From 0.1 to 10
  msg.pitch = 1; // From 0 to 2
  msg.text = props.text;
  msg.lang = "en";
  console.log({msg});
  speechSynthesis.speak(msg);
}
</script>

<template>
  <button
    border="r gray-400 opacity-50"
    p="2"
    font="mono"
    outline="!none"
    hover:bg="gray-400 opacity-20"
    @click="speakUtterance"
  >
    <carbon:play-filled />
  </button>
  <!-- <form action="">
    <input type="slid" />
  </form> -->
  <!-- <select name="" id="">
    <option :value="voice" v-for="voice in voices">
      {{ voice }}
    </option>
  </select> -->
</template>
