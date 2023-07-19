<template>
  <q-layout view="lHh lpR fFf">
    <q-header reveal bordered class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <Logo />
        </q-toolbar-title>
        <q-btn no-caps flat icon="logout" size="lg" @click="goToLoginPage"
          ><q-tooltip class="bg-primary text-body2"> Logout </q-tooltip></q-btn
        >
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from "vue";
import Logo from "/src/components/App-Logo.vue";

export default {
  components: {
    Logo,
  },
  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
  methods: {
    goToLoginPage() {
      this.$router.push("/"); // Navigate to the '/home' route
    },
  },
};
</script>
