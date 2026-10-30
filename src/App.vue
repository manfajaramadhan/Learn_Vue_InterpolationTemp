<script setup>
import { ref, computed } from "vue";

const name = ref("Fluffy Sky Coat");
const slugtext = ref("The Quick #(*!&@ Brown 29");

const slugetize = computed(() => {
  return slugtext.value
    .toLowerCase()
    .replace(/[^\w ]+/g, "")
    .replace(/ +/g, "-");
});

function now() {
  const date = new Date();

  return (
    String(date.getHours()).padStart(2, "0") +
    ":" +
    String(date.getMinutes()).padStart(2, "0") +
    ":" +
    String(date.getSeconds()).padStart(2, "0")
  );
}
</script>

<template>
  <div class="container">
    <h3>Interpolation</h3>
    <br />

    <p>
      <strong>Bound : </strong><br />
      <span>{{ name }}</span>
    </p>

    <p>
      <strong>Parsed : </strong><br />
      <span v-html="name"></span>
    </p>

    <p>
      <strong>Unchangeable : </strong><br />
      <span v-once>{{ name }}</span>
    </p>

    <h5>Text</h5>

    <textarea class="form-control" rows="3" v-model="name"></textarea>
  </div>

  <br />

  <div>
    <div class="container">
      <h3>Slugtize</h3>
      <br />
      <input type="text" class="form-control" v-model="slugtext" />
      <div class="font-weight text-danger">
        {{ slugetize }}
      </div>
      <div>Last changed: {{ now() }}</div>
    </div>
  </div>
</template>

<style scoped></style>
