
<template>
  <div id="app">
    <nav class="navbar navbar-expand-md align-items-center">
      <div class="container">
        <div class="col text-center text-md-left">
          <a class="navbar-brand" href="#">Coin Market Gene</a>
        </div>
        <div class="col">
          <form class="form-inline form_search">
            <div class="input-group">
              <input
                class="form-control"
                type="search"
                placeholder="Search"
                aria-label="Search"
                aria-describedby="button-addon"
              >
              <div class="input-group-append">
                <button class="btn btn-icon" type="button" id="button-addon">
                  <i class="icon icon--search"></i>
                </button>
              </div>
            </div>
          </form>
        </div>
        <div class="col text-right">
          <button
            class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
              <ul class="navbar-nav ml-auto">
                <li v-bind:class="{ 'nav-item active':thepath=='/', 'nav-item':thepath!='/'}">
                  <router-link class="nav-link" to="/">Home</router-link>
                </li>
                <li
                  v-bind:class="{ 'nav-item active':thepath=='/metrics', 'nav-item':thepath!='/metrics'}"
                >
                  <router-link class="nav-link" to="/metrics">Metrics</router-link>
                </li>
                <li
                  v-bind:class="{ 'nav-item active':thepath=='/about', 'nav-item':thepath!='/about'}"
                >
                  <router-link class="nav-link" to="/about">About</router-link>
                </li>
              </ul>
          </div>
        </div>
      </div>
    </nav>
    <div class="main">
      <div class="container">
        <router-view/>
      </div>
    </div>

    <div class="footer">
      <div class="container">
        <div class="footer_wrapper">
          <div class="row align-items-center">
            <div class="col-6">
              <div class="copy">© 2018</div>
            </div>
            <div class="col-6 text-right">
              <div class="social">
                <a href="#" target="_blank" class="social__link"><i class="icon icon--facebook"></i></a>
                <a href="#" target="_blank" class="social__link"><i class="icon icon--twitter"></i></a>
                <a href="#" target="_blank" class="social__link"><i class="icon icon--reddit"></i></a>
                <a href="#" target="_blank" class="social__link"><i class="icon icon--telegram"></i></a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",

  data() {
    return {
      thepath: "---"
    };
  },

  methods: {
    handleStyles() {
      console.log(this.$route.path);
      this.thepath = this.$route.path;
    }
  },
  // Handle styles when the app is initially loaded
  mounted() {
    this.handleStyles();
  },
  // Handle styles when the route changes
  watch: {
    $route() {
      this.handleStyles();
    }
  }
};
</script>

<style lang="scss">
@import "~bootstrap/scss/functions";
@import "~bootstrap/scss/variables";
$primary: #003cff !default;
@import "~bootstrap/scss/mixins";
@import "~bootstrap/scss/utilities";
@import "~bootstrap/scss/reboot";
@import "~bootstrap/scss/type";
@import "~bootstrap/scss/grid";
@import "~bootstrap/scss/tables";
@import "~bootstrap/scss/forms";
@import "~bootstrap/scss/buttons";
@import "~bootstrap/scss/transitions";
@import "~bootstrap/scss/dropdown";
@import "~bootstrap/scss/button-group";
@import "~bootstrap/scss/input-group";
@import "~bootstrap/scss/custom-forms";
@import "~bootstrap/scss/tooltip";
@import "~bootstrap/scss/popover";
@import "~bootstrap/scss/list-group";
@import "~bootstrap/scss/card";
@import "~bootstrap/scss/nav";
@import "~bootstrap/scss/navbar";
@import "~bootstrap/scss/badge";

@import "styles/common/fonts";
@import "styles/common/vars";
@import "styles/common/functions";
@import "styles/common/mixins";
@import "styles/common/typo";

* {
  box-sizing: border-box;
}

html {
  min-height: 100%;
  overflow: visible !important;
  font-size: 1rem;
  position: relative;

  @media (#{$max_laptop--small}) {
    font-size: 12px;
  }

  @media (#{$max_phones}) {
    font-size: 10px;
  }
}

body {
  font: 400 rem(getFontSize(regular)) $font-default;
  color: getColor(text);
  background-color: getColor(white);
  line-height: normal;
  position: static;
  -webkit-overflow-scrolling: touch;

  -webkit-text-size-adjust: none;
  font-size-adjust: none;
  text-rendering: optimizeLegibility;

  @include fontantialias(true);
}

.container {
  width: 1220px + 30px;
  max-width: 100%;
}

[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}

.main {
  padding-bottom: rem(96px);
}

.content {
  padding-bottom: rem(40px);
}

.text-success {
  color: getColor(green) !important;
}

.text-danger {
  color: getColor(red) !important;
}

@import "styles/partials/header";
@import "styles/partials/footer";
@import "styles/partials/forms";
@import "styles/partials/filter";
@import "styles/partials/table";
@import "styles/partials/price";
</style>
