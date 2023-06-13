<template>
  <div class="container">
    <form class="row g-3">
      <div class="col-auto">
        <label for="staticEmail2" class="visually-hidden">Email</label>
        <input
          type="text"
          class="form-control"
          id="staticEmail2"
          placeholder="email@example.com"
          v-model="email"
        />
      </div>
      <div class="col-auto">
        <label for="inputPassword2" class="visually-hidden">Password</label>
        <input
          type="password"
          class="form-control"
          id="inputPassword2"
          placeholder="Password"
          v-model="password"
        />
      </div>
      <div class="col-auto">
        <button type="submit" class="btn btn-primary mb-3" @click="authUser">
          Submit
        </button>
      </div>
      <div>{{ email }}</div>
      <div>{{ password }}</div>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import AuthService from "../services/AuthService";
let email = ref("");
let password = ref("");

const auth = new AuthService();
auth.login(email.value, password.value);

const authUser = async () => {
  const auth = new AuthService();
  const success = await auth.login(email.value, password.value);
  if (success) {
    alert("Exito en el Login!");
  } else {
    alert("Login incorrecto");
  }
};
</script>
