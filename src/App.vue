<template>
  <div class="container">
    <div class="p-10">
      <h3 class="mb-10">Formulaire</h3>
      <form>
        <input class="mr-10" type="text" placeholder="Prénom" />
        <input class="mr-10" type="text" placeholder="Email" />
        <button>Sauvegarder</button>
      </form>
    </div>
    <div class="p-20">
      <h3>Liste des utilisateurs</h3>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useForm, useField } from 'vee-validate';
import { reactive } from 'vue';

interface User {
  name: string;
  email: string;
  createdAt?: string;
  _id?: string;
}

const state = reactive({
  users: [],
});

const { handleSubmit } = useForm();

const mySubmit = handleSubmit(async (value) => {
  try {
    const response = await fetch('https://restapi.fr/api/vueuser', {
      method: 'POST',
      body: JSON.stringify(values),
      headers: {
        'Content-Type': 'application/json',
      },
    });
    const user = await response.json();
  } catch (err) {
    console.error(err);
  }
});

const { value: emailValue } = useField('email');
const { value: name } = useField('name');
</script>

<style lang="scss">
@import './assets/scss/base.scss';
</style>
