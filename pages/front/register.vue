<template>
  <div id="main-wrapper" class="oxyy-login-register">
    <div class="hero-wrap d-flex align-items-center h-100">
      <div class="hero-mask opacity-4 bg-secondary"></div>
      <div class="hero-bg hero-bg-scroll"></div>
      <div class="hero-content mx-auto w-100 h-100">
        <b-container>
          <b-row no-gutters class="min-vh-100">
            <b-col md="6" class="d-flex flex-column">
              <b-row no-gutters class="my-auto">
                <b-col cols="10" lg="9" class="mx-auto text-center">
                  <div class="logo mt-5 mb-3">
                    <a href="javascript:void(0)" title="Oxyy"
                      ><img src="images/logo-lg-light.png"
                    /></a>
                  </div>
                  <h1 class="text-5 font-weight-400 text-white mb-5">
                    Looks like you're new here!
                  </h1>
                  <h2 class="text-white line-height-3 mb-5">
                    Join our group in few minutes! Sign up with your details to
                    get started
                  </h2>
                </b-col>
              </b-row>
            </b-col>

            <b-col md="6" class="d-flex align-items-center py-5">
              <b-container class="my-auto py-4 bg-white">
                <b-row>
                  <b-col cols="11" lg="11" class="mx-auto">
                    <h3 class="text-9 font-weight-600 text-center mt-2 mb-3">
                      Create an Account
                    </h3>
                    <p class="text-center mb-4">
                      Already have an account?
                      <nuxt-link to="/front/login" class="btn-link" no-prefetch
                        ><u>Sign In</u></nuxt-link
                      >
                    </p>
                    <form id="registerForm" method="post">
                      <div class="form-group">
                        <label
                          class="text-dark font-weight-600"
                          for="emailAddress"
                          >Email Address</label
                        >
                        <input
                          id="emailAddress"
                          type="email"
                          class="form-control rounded-0"
                          required
                          placeholder="Enter Your Email"
                        />
                      </div>
                      <div class="form-group">
                        <label
                          class="text-dark font-weight-600"
                          for="emailAddress"
                          >Username</label
                        >
                        <input
                          id="emailAddress"
                          type="email"
                          class="form-control rounded-0"
                          required
                          placeholder="Enter Your Email"
                        />
                      </div>
                      <div class="form-group">
                        <label
                          class="text-dark font-weight-600"
                          for="loginPassword"
                          >Password</label
                        >
                        <b-input-group>
                          <b-form-input
                            :id="`loginPassword`"
                            :type="togglePassword ? 'text' : 'password'"
                            placeholder="Enter Password"
                            required
                          ></b-form-input>
                          <b-input-group-append>
                            <span
                              class="input-group-text"
                              @click="togglePassword = !togglePassword"
                              ><i
                                :class="
                                  !togglePassword
                                    ? 'far fa-eye'
                                    : 'far fa-eye-slash'
                                "
                              ></i
                            ></span>
                          </b-input-group-append>
                        </b-input-group>
                      </div>
                      <button
                        class="btn btn-dark btn-block rounded-0 my-4"
                        type="submit"
                      >
                        Create Account
                      </button>
                    </form>
                    <div class="d-flex align-items-center my-3">
                      <hr class="flex-grow-1" />
                      <span class="mx-2 text-2 text-muted">Or create with</span>
                      <hr class="flex-grow-1" />
                    </div>
                    <div class="form-row mb-3">
                      <div class="col-4">
                        <button
                          type="button"
                          class="btn btn-outline-facebook btn-sm btn-block border-2 rounded-0 shadow-none"
                        >
                          <span class="mr-2"
                            ><i class="fab fa-facebook-f"></i></span
                          >Facebook
                        </button>
                      </div>
                      <div class="col-4">
                        <button
                          type="button"
                          class="btn btn-outline-google btn-sm btn-block border-2 rounded-0 shadow-none"
                        >
                          <span class="mr-2"><i class="fab fa-google"></i></span
                          >Google
                        </button>
                      </div>
                      <div class="col-4">
                        <button
                          type="button"
                          class="btn btn-outline-twitter btn-sm btn-block border-2 rounded-0 shadow-none"
                        >
                          <span class="mr-2"
                            ><i class="fab fa-twitter"></i></span
                          >twitter
                        </button>
                      </div>
                    </div>
                  </b-col>
                </b-row>
              </b-container>
            </b-col>
          </b-row>
        </b-container>
      </div>
    </div>
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
      title: 'Register',
    }
  },
}
</script>

<style scoped>
.hero-bg {
  background-image: url('/vendor/front-page/images/login-bg-3.jpg');
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
