<template>
  <q-card flat class="bg-color">
    <q-card-section class="q-py-xs">
      <Logo />
    </q-card-section>
    <q-card-actions vertical class="q-pt-lg">
      <q-btn
        class="q-my-lg"
        outline
        rounded
        color="white"
        label="Sign in"
        @click="$emit('changeCard', 'login')"
      />
      <q-btn
        class="q-mt-lg"
        outline
        rounded
        color="white"
        label="Create Account"
        @click="$emit('changeCard', 'create')"
      />
    </q-card-actions>

    <!-- <q-separator class="q-mt-lg" color="white" /> -->
    <q-card-actions class="q-mt-lg" align="center">
      <q-btn flat round color="white">
        <q-icon size="lg" class="fab fa-facebook"></q-icon
      ></q-btn>
      <q-btn flat round color="white">
        <q-icon size="lg" class="fab fa-twitter"></q-icon
      ></q-btn>
      <q-btn flat round color="white">
        <q-icon size="lg" class="fab fa-instagram"></q-icon>
      </q-btn>
    </q-card-actions>
    <q-card-actions class="q-mt-lg" align="center">
      <q-btn flat color="white">
        Contact Us
        <q-icon size="md" class="q-pl-sm far fa-envelope"></q-icon>
      </q-btn>
    </q-card-actions>
  </q-card>
</template>
<script>
import Logo from "/src/components/App-Logo.vue";

export default {
  name: "LandingMenu",
  components: {
    Logo,
  },
};
</script>
