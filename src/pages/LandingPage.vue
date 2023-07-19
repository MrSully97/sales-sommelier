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
        <q-card flat class="bg-color">
          <q-card-actions align="right">
            <div class="text-h4 text-white fancy-text">Login</div>
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
            Please fill in your credentials to login.
            <q-input
              class="q-py-sm"
              style="width: 250px"
              v-model="username"
              label="Username"
              color="white"
              outlined
              clearable
              label-color="darkred"
            />
            <q-input
              class="q-py-xs"
              style="width: 250px"
              v-model="password"
              label="Password"
              type="password"
              color="white"
              outlined
              clearable
              label-color="darkred"
            />
            <q-card-section class="q-py-xs" align="right"
              ><q-btn
                flat
                no-caps
                size="sm"
                label="Forgot Password?"
                @click="forgotPasswordDialog = true"
              />
            </q-card-section>
          </q-card-actions>
          <q-card-actions class="q-py-xs">
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
      <div v-else-if="showCard === 3" key="card3">
        <q-card flat class="bg-color">
          <q-card-actions align="right">
            <div class="q-pr-md text-white fancy-text-small">
              Create Account
            </div>
            <q-space />
            <q-btn
              class="red-button"
              @click="showCard = 1"
              flat
              round
              icon="arrow_back"
            />
          </q-card-actions>
          <q-card-actions vertical class="q-pt-lg" align="center">
            Fill in information below to create an account.

            <q-input
              class="q-py-sm"
              style="width: 250px"
              v-model="username"
              label="Username"
              color="white"
              outlined
              clearable
              label-color="darkred"
            />
            <q-input
              class="q-py-sm"
              style="width: 250px"
              v-model="email"
              label="Email"
              color="white"
              outlined
              clearable
              label-color="darkred"
            />
            <q-input
              class="q-py-xs"
              style="width: 250px"
              v-model="password"
              label="Password"
              type="password"
              color="white"
              outlined
              clearable
              label-color="darkred"
            />
            <q-input
              class="q-py-xs"
              style="width: 250px"
              v-model="confirmPassword"
              label="Confirm Password"
              type="password"
              color="white"
              outlined
              clearable
              label-color="darkred"
            />
          </q-card-actions>

          <q-card-actions vertical class="q-pt-sm" align="center">
            <q-btn
              @click="verifyEmailDialog = true"
              style="width: 250px"
              label="Create Account"
              class="q-mt-md red-button"
            />
          </q-card-actions>
        </q-card>
      </div>
    </transition>
    <!-- Forgot Password Dialog -->
    <q-dialog v-model="forgotPasswordDialog" persistent>
      <transition
        mode="out-in"
        enter-active-class="animated fadeInRight"
        leave-active-class="animated fadeOutLeft"
      >
        <!-- Password Reset card -->
        <q-card
          style="background: white"
          v-if="showForgotCard === 1"
          key="forgotCard1"
        >
          <q-card-actions align="right">
            <div class="fancy-text-small">Reset Password</div>
            <q-space />
            <q-btn
              class="white-button"
              round
              icon="close"
              v-close-popup
              @click="showForgotCard = 1"
            />
          </q-card-actions>

          <q-card-section vertical style="color: black">
            Enter the email associated with your account and we'll send an email
            with instructions to reset your password.
            <q-input
              class="q-py-xs input-red"
              v-model="forgotEmail"
              label="Email"
              color="white"
              bg-color="primary"
              outlined
              clearable
            />
          </q-card-section>

          <q-card-actions align="center">
            <q-btn
              class="white-button"
              no-caps
              flat
              @click="showForgotCard = 2"
              label="Send Instructions"
            />
          </q-card-actions>
        </q-card>
        <!-- Confirmation of password reset card-->
        <q-card
          style="background: white"
          v-else-if="showForgotCard === 2"
          key="forgotCard2"
        >
          <q-card-actions align="center">
            <q-icon color="primary" size="100px" name="mark_as_unread" />
          </q-card-actions>

          <q-card-section align="center" style="color: black">
            <div class="fancy-text-small">Check Your Email</div>
            We have sent password recovery instructions to your email.
          </q-card-section>

          <q-card-actions align="center">
            <q-btn
              class="white-button"
              no-caps
              flat
              label="Close"
              @click="
                showForgotCard = 1;
                forgotPasswordDialog = false;
              "
              v-close-popup
            />
          </q-card-actions>
        </q-card>
      </transition>
    </q-dialog>
    <!-- Verify Email Dialog -->
    <q-dialog v-model="verifyEmailDialog" persistent>
      <!-- Confirmation of password reset card-->
      <q-card style="background: white">
        <q-card-actions align="center">
          <q-icon color="primary" size="100px" name="mark_as_unread" />
        </q-card-actions>

        <q-card-section align="center" style="color: black">
          <div class="fancy-text-small">Check Your Email</div>
          We have sent you an email to verify your account.
        </q-card-section>

        <q-card-actions align="center">
          <q-btn
            class="white-button"
            no-caps
            flat
            label="Close"
            @click="
              verifyEmailDialog = false;
              showCard = 1;
            "
            v-close-popup
          />
        </q-card-actions>
      </q-card>
    </q-dialog>
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
      showForgotCard: 1,
      rememberMeBox: false,
      forgotPasswordDialog: false,
      verifyEmailDialog: false,
      username: "",
      email: "",
      forgotEmail: "",
      password: "",
      confirmPassword: "",
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
