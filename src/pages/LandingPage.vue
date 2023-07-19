<template>
  <q-page
    class="bg-color window-height window-width row justify-center items-center"
  >
    <transition
      mode="out-in"
      enter-active-class="animated fadeInLeft"
      leave-active-class="animated fadeOutRight"
    >
      <!-- Landing Menu -->
      <LandingMenu
        v-if="currentCard === 'menu'"
        key="menu"
        @changeCard="changeCard"
      />
      <!-- Login Page -->
      <LoginCard
        v-else-if="currentCard === 'login'"
        key="login"
        @changeCard="changeCard"
      />
      <!-- Create Page -->
      <CreateCard
        v-else-if="currentCard === 'create'"
        key="create"
        @changeCard="changeCard"
      />
    </transition>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import LandingMenu from "/src/components/LandingMenu.vue";
import LoginCard from "/src/components/LoginCard.vue";
import CreateCard from "/src/components/CreateCard.vue";

export default defineComponent({
  name: "LandingPage",
  components: {
    LandingMenu,
    LoginCard,
    CreateCard,
  },
  data() {
    return {
      currentCard: "menu",
    };
  },
  methods: {
    changeCard(cardName) {
      this.currentCard = cardName;
    },
  },
});
</script>

<style>
.bg-color {
  background-color: darkred;
}

.red-button {
  color: darkred;
  background-color: white;
}

.white-button {
  color: white;
  background-color: darkred;
}

.fancy-text {
  font-size: 45px;
  font-family: "Marck Script", cursive;
}

.fancy-text-small {
  font-size: 35px;
  font-family: "Marck Script", cursive;
  color: darkred;
}
</style>
