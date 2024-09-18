<template>
  <div class="background-container">
    <v-img
      class="mx-auto my-6"
      max-width="228"
      max-height="128"
      src="https://www.kindpng.com/picc/m/125-1256447_batman-logo-png-black-transparent-background-hd-print.png"
    ></v-img>

    <v-card
      class="mx-auto pa-12 pb-8 blurred-background"
      elevation="8"
      max-width="448"
      rounded="lg"
    >
      <div class="text-subtitle-1 text-medium-emphasis">Account</div>

      <v-text-field
        v-model="email"
        density="compact"
        placeholder="Email address"
        prepend-inner-icon="mdi-email-outline"
        variant="outlined"
      ></v-text-field>

      <div
        class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between"
      >
        Password

        <a
          class="text-caption text-decoration-none text-blue"
          href="#"
          rel="noopener noreferrer"
          target="_blank"
        >
          Forgot login password?</a
        >
      </div>

      <v-text-field
        v-model="password"
        :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
        :type="visible ? 'text' : 'password'"
        density="compact"
        placeholder="Enter your password"
        prepend-inner-icon="mdi-lock-outline"
        variant="outlined"
        @click:append-inner="visible = !visible"
      ></v-text-field>

      <v-card class="mb-12" color="surface-variant" variant="tonal">
        <v-card-text class="text-medium-emphasis text-caption">
          Warning: After 3 consecutive failed login attempts, you account will
          be temporarily locked for three hours. If you must login now, you can
          also click "Forgot login password?" below to reset the login password.
        </v-card-text>
      </v-card>

      <v-btn @click="doLogin" class="mb-8" color="blue" size="large" variant="tonal" block>
        Log In
      </v-btn>

      <v-card-text class="text-center">
        <a
          class="text-blue text-decoration-none"
          href="signup"
          rel="noopener noreferrer"
          target="_blank"
        >
          Sign up now <v-icon icon="mdi-chevron-right"></v-icon>
        </a>
      </v-card-text>
    </v-card>
  </div>
</template>
<script>
  definePageMeta({
    layout: "custom",
  });

  import axios from 'axios';
export default {

  data: () => ({
    visible: false,
    email: "",
    password: ""
  }),
  methods: {
    async doLogin() {
      let forms = {
      email: this.email,
      password: this.password
    }  
    console.log(this.email)
    console.log(forms.password)
    console.log(forms)
    const res = await axios.post('http://localhost:7000/login', forms)
    const data = await res.data
    console.log(data.status)
    if (data.status == 'success') {
      console.log(data.row.email)
      // window.sessionStorage.setItem("user", JSON.stringify(data.row.email)); // แบบนี้หาย เมื่อ restart หรือ ปิด  browser
      window.sessionStorage.setItem("token", JSON.stringify(data.token));
      this.$router.replace('/home')

    }else{
      this.$router.replace('/login')
    }
  }
  }
};
</script>


<!-- <style scoped>
.background-container {
  min-height: 100vh;
  background-image: url('https://png.pngtree.com/background/20230317/original/pngtree-beautiful-background-of-starry-sky-at-night-picture-image_2148622.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  overflow: hidden;
  position: relative; /* Required for absolute positioning of the overlay */
}

.blurred-background {
  backdrop-filter: blur(20px); /* Apply blur effect */
  -webkit-backdrop-filter: blur(20px); /* For Safari support */
  background: rgba(255, 255, 255, 0.6); /* Semi-transparent white background for contrast */
}
</style> -->
