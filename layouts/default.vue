<template>
  <v-app>
    <no-ssr>
      <notifications group="notify" />
    </no-ssr>
    <v-content>
      <v-toolbar color="indigo" dark>
        <v-toolbar-side-icon></v-toolbar-side-icon>
        <v-toolbar-title>
          <n-link to="/">Learning Nuxt</n-link>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn flat>
            <n-link to="/weather-app">Weather App</n-link>
          </v-btn>
          <v-btn flat>
            <n-link to="/quiz">Quiz App</n-link>
          </v-btn>
          <v-btn v-if="$auth()" flat @click="logout">
            Logout
          </v-btn>
        </v-toolbar-items>
      </v-toolbar>
      <transition>
        <nuxt />
      </transition>
    </v-content>
  </v-app>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$cookies.remove('token')
      this.$store.commit('auth/setLoggedIn', false)
      this.$router.push('/admin/login')
    }
  }
}
</script>

<style>
a {
  text-decoration: none;
  color: white;
}
</style>
