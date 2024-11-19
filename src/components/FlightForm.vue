<script setup lang="ts">
import {reactive} from "vue";
import {Flight} from "../types/flight.ts";

const props = defineProps<{flight?: Flight}>();
const flightForm = reactive<Flight>(props.flight ?? {
  id: "",
  name: "",
  departure: "",
  destination: ""
});
</script>

<template>
  <form @submit.prevent="$emit('submit', flightForm)">
    <div class="input-section">
      <p>Name:</p>
      <input type="text" v-model="flightForm.name" required />
    </div>
    <div class="input-section">
      <p>Departure:</p>
      <input type="text" v-model="flightForm.departure" required >
    </div>
    <div class="input-section">
      <p>Destination:</p>
      <input type="text" v-model="flightForm.destination" required >
    </div>
    <div class="form-buttons">
      <button type="button" @click="$emit('cancel')" class="cancel-button">Cancel</button>
      <button type="submit" class="submit-button">Apply changes</button>
    </div>

  </form>
</template>

<style scoped>
  form {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .input-section {
    display: flex;
    flex-direction: column;
  }

  p {
    font-size: 1.5rem;
    color: #b1ffdc;
  }

  input {
    background: #b1ffdc;
    border: none;
    border-radius: 0.3rem;
    font-size: 1.5rem;
    padding: 0.2rem;
  }

  .form-buttons {
    width: 25%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    margin: 2rem;
  }

  button {
    height: 2rem;
    width: 45%;
  }
</style>