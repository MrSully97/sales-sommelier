<template>
  <div class="q-pa-md">
    <q-input outlined v-model="email" label="Email" />
    <q-input outlined v-model="password" label="Password" type="password" />
    <q-btn @click="login" color="primary" label="Login" class="q-mt-md" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    login() {
      // Add your login logic here
      console.log("Login clicked");
    },
  },
};
</script>
