<template>
  <!-- Preloader -->
  <div v-if="loading" class="preloader">
    <div class="lds-ellipsis">
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </div>
  </div>
  <!-- Preloader End -->
</template>

<script>
export default {
  data() {
    return {
      loading: true,
    }
  },
  mounted() {
    if (process.browser) {
      window.onNuxtReady((app) => {
        // eslint-disable-next-line
        this.loading = false
      })
    }
  },
  head() {
    return {
      link: [
        {
          rel: 'stylesheet',
          type: 'text/css',
          href:
            'https://fonts.googleapis.com/css?family=Poppins:100,200,300,400,500,600,700,800,900',
        },
        {
          rel: 'stylesheet',
          type: 'text/css',
          href: '/vendor/font-awesome5/css/all.min.css',
        },
        {
          rel: 'stylesheet',
          type: 'text/css',
          href: '/vendor/front-page/css/stylesheet.css',
        },
      ],
    }
  },
}
</script>
