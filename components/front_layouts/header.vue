<template>
  <!-- Preloader -->
  <div class="preloader">
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
      title: 'Hello World!',
    }
  },
  head() {
    return {
      title: 'Monolith - Login',
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
          href: '/vendor/bootstrap4/css/bootstrap.min.css',
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
      script: [
        { src: '/vendor/bootstrap4/js/bootstrap.bundle.min.js' },
        { src: '/vendor/front-page/js/theme.js' },
      ],
    }
  },
}
</script>
