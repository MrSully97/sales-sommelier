<template>
  <q-page
    class="bg-color window-height window-width row justify-center items-center"
  >
    <transition
      mode="out-in"
      enter-active-class="animated fadeInLeft"
      leave-active-class="animated fadeOutRight"
    >
      <!-- Landing Page -->
      <q-card flat class="bg-color" v-if="showCard === 1" key="card1">
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
            @click="showCard = 2"
          />
          <q-btn
            class="q-mt-lg"
            outline
            rounded
            color="white"
            label="Create Account"
            @click="showCard = 3"
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

      <!-- Login Page -->
      <div v-else-if="showCard === 2" key="card2">
        <q-card flat>
          <q-card-actions align="right">
            <div class="text-h4">Login</div>
            <q-space />
            <q-btn
              class="red-button"
              @click="showCard = 1"
              flat
              round
              icon="arrow_back"
            />
          </q-card-actions>
          <q-card-actions vertical class="q-pt-lg">
            <q-input
              class="q-py-sm"
              v-model="email"
              label="Email"
              color="red"
              outlined
              label-color="darkred"
            />
            <q-input
              class="q-py-sm"
              v-model="password"
              label="Password"
              type="password"
              color="red"
              outlined
              label-color="darkred"
            />
          </q-card-actions>
          <q-card-actions class="q-pt-xs">
            <q-checkbox
              v-model="rememberMeBox"
              color="black"
              label="Remember me"
            />
          </q-card-actions>
          <q-card-actions vertical class="q-pt-sm">
            <q-btn @click="login" label="Login" class="q-mt-md red-button" />
          </q-card-actions>
        </q-card>
      </div>
      <!-- Create Page -->
      <q-card flat v-else-if="showCard === 3" key="card3">
        <q-card-section>
          <div class="q-pa-md">
            <q-input outlined v-model="email" label="Email" />
            <q-input
              outlined
              v-model="password"
              label="Password"
              type="password"
            />
            <q-btn
              @click="login"
              color="primary"
              label="Login"
              class="q-mt-md"
            />
          </div>
          <q-btn @click="showCard = 1" label="Back" color="primary" />
        </q-card-section>
      </q-card>
    </transition>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import Logo from "/src/components/App-Logo.vue";

export default defineComponent({
  name: "LandingPage",
  components: {
    Logo,
  },
  data() {
    return {
      showCard: 1,
      rememberMeBox: false,
    };
  },
  methods: {
    changePage(page) {
      switch (page) {
        case "LandingPage":
          this.showLandingCard = true;
          this.showLoginCard = false;
          this.showCreateCard = false;
          break;
        case "LoginPage":
          this.showLandingCard = false;
          this.showLoginCard = true;
          this.showCreateCard = false;
          break;
        case "CreatePage":
          this.showLandingCard = false;
          this.showLoginCard = false;
          this.showCreateCard = true;
          break;
      }
    },
  },
});
</script>

<style>
.bg-color {
  background-color: darkred;
}

.red-button {
  color: white;
  background-color: darkred;
}
</style>
