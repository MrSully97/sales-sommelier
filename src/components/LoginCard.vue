<template>
  <q-card flat class="bg-color">
    <q-card-actions align="right">
      <div class="text-h4 text-white fancy-text">Login</div>
      <q-space />
      <q-btn
        class="red-button"
        @click="$emit('changeCard', 'menu')"
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
      <q-checkbox v-model="rememberMeBox" color="black" label="Remember me" />
    </q-card-actions>
    <q-card-actions vertical class="q-pt-sm">
      <q-btn label="Login" class="q-mt-md red-button" @click="goToHomePage" />
    </q-card-actions>
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
  </q-card>
</template>
<script>
export default {
  name: "LoginCard",
  data() {
    return {
      showForgotCard: 1,
      rememberMeBox: false,
      forgotPasswordDialog: false,
      verifyEmailDialog: false,
      username: "",
      email: "",
      forgotEmail: "",
      password: "",
    };
  },
  methods: {
    goToHomePage() {
      this.$router.push("/home"); // Navigate to the '/home' route
    },
  },
};
</script>
