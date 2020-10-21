<template>
  <div id="main-wrapper" class="oxyy-login-register">
    <b-container fluid class="px-0">
      <b-row no-gutters class="min-vh-100">
        <!-- Welcome Text
        ========================= -->
        <b-col md="6">
          <div class="hero-wrap d-flex align-items-center h-100">
            <div class="hero-mask opacity-8 bg-primary"></div>
            <div class="hero-bg hero-bg-scroll"></div>
            <div class="hero-content mx-auto w-100 h-100 d-flex flex-column">
              <div class="row no-gutters">
                <div class="col-10 col-lg-9 mx-auto">
                  <div class="logo mt-5 mb-5 mb-md-0">
                    <a class="d-flex" href="javascript:void(0)" title="logo"
                      ><img
                        src="/vendor/front-page/images/logo-light.png"
                        alt="logo"
                    /></a>
                  </div>
                </div>
              </div>
              <div class="row no-gutters my-auto">
                <div class="col-10 col-lg-9 mx-auto">
                  <h1 class="text-11 text-white mb-4">Welcome back!</h1>
                  <p class="text-4 text-white line-height-4 mb-5">
                    We are glad to see you again! Get access to your Orders,
                    Wishlist and Recommendations.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </b-col>
        <!-- Welcome Text End -->

        <!-- Login Form
        ========================= -->
        <b-col md="6" class="d-flex align-items-center">
          <b-container fluid class="my-auto py-5">
            <b-row>
              <b-col cols="11" lg="9" xl="8" class="mx-auto">
                <h3 class="font-weight-600 mb-2">Reset Your password</h3>
                <p class="mb-4">
                  Please enter your email address and we will send you a
                  password password link.
                </p>
                <form id="loginForm" method="post">
                  <div class="form-group">
                    <label for="emailAddress">Email Address</label>
                    <b-form-input
                      :id="`emailAddress`"
                      placeholder="Enter username or email"
                      required
                    ></b-form-input>
                  </div>
                  <b-button block variant="primary" type="submit" class="my-4"
                    >Reset Password</b-button
                  >
                </form>
                <p class="text-center text-muted">
                  Already have an account?
                  <nuxt-link to="/front/login" class="btn-link" no-prefetch
                    ><u>Sign In</u></nuxt-link
                  >
                </p>
              </b-col>
            </b-row>
          </b-container>
        </b-col>
        <!-- Login Form End -->
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { mapMutations } from 'vuex'
export default {
  layout: 'front',
  auth: false,
  data() {
    return {
      auth: {
        email: null,
        password: null,
      },
      togglePassword: false,
    }
  },
  mounted() {
    if (this.$auth.loggedIn) {
      this.$router.push('/')
    }
  },
  methods: {
    ...mapMutations(['SET_IS_AUTH']),
    submit() {
      this.$auth
        .loginWith('local', {
          data: {
            email: this.auth.email,
            password: this.auth.password,
          },
        })
        .then(() => {
          this.SET_IS_AUTH(true)
          this.$router.push('/')
        })
    },
  },
  head() {
    return {
      title: 'Forgot Password',
    }
  },
}
</script>

<style scoped>
.hero-bg {
  background-image: url('/vendor/front-page/images/login-bg.jpg');
}
#loginPassword {
  border-right: none;
}
.input-group-text {
  width: 48px;
  cursor: pointer;
  border-left: none;
  background-color: #ffffff;
}
[class^='far-'],
[class*=' fa-'] {
  display: inline-block;
  width: 100%;
}
</style>
