<template>
  <q-card flat class="bg-color">
    <q-card-actions align="right">
      <div class="q-pr-md text-white fancy-text-small">Create Account</div>
      <q-space />
      <q-btn
        class="red-button"
        @click="$emit('changeCard', 'menu')"
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
  </q-card>
</template>
<script>
export default {
  name: "CreateCard",
  data() {
    return {
      username: "",
      email: "",
      forgotEmail: "",
      password: "",
      confirmPassword: "",
      verifyEmailDialog: false,
    };
  },
};
</script>
