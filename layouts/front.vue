<template>
  <b-container fluid class="p-0">
    <app-header />
    <nuxt />
  </b-container>
</template>

<script>
import { mapState } from 'vuex'
import Header from '~/components/front_layouts/Header.vue'

export default {
  components: {
    'app-header': Header,
  },
  data() {
    return {
      // isAuth: false
    }
  },
  computed: {
    ...mapState(['isAuth']),
  },
}
</script>
