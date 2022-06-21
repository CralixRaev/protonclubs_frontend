<template>
  <v-app>

    <v-app-bar app>
      <v-app-bar-title>
        Протон - кружки
      </v-app-bar-title>
    </v-app-bar>
    <v-main>
      <v-container fluid>

        <!-- If using vue-router -->
        <Suspense>
        <template #default>
          <router-view></router-view>
        </template>
        <template #fallback>
          Loading...
        </template>
        </Suspense>
      </v-container>
    </v-main>

    <v-footer app>
      <!-- -->
    </v-footer>
  </v-app>
</template>

<style>
</style>
<script>
export default {
  components: {}
}
</script>