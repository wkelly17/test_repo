<script setup lang="ts">
import {ref} from "vue";

let chars: any = [];
for (let i = 0; i < 26; i++) {
  let letter = (i + 10).toString(36);
  let bl = letter.toUpperCase();
  chars.push([bl, letter]);
}
</script>

<template>
  <span v-for="char in chars" class="leading-loose">
    <span class="whitespace-nowrap">
      {{ char[0] }}
      <span class="text-red-400 inline-block mr-4"> {{ char[1] }}</span>
    </span>
  </span>
</template>
