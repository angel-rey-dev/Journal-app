<template>
  <template v-if="authStatus === 'authenticating'">
    <LoadingSpinner />
  </template>
  <router-view v-else />
</template>

<script>
import useAuth from "@/modules/auth/composables/useAuth";
import { defineAsyncComponent } from "vue";

export default {
  name: "App",
  components: {
    LoadingSpinner: defineAsyncComponent(() =>
      import("@/components/LoadingSpinner")
    ),
  },
  setup() {
    const { authStatus, checkAuthStatus } = useAuth();
    checkAuthStatus();
    return {
      authStatus,
    };
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@300;500;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: "Raleway", Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow-x: hidden;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
