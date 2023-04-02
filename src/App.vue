<template>
  <v-app theme="dark">
    <toolbar />

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import Toolbar from "@/components/toolbar.vue";
</script>
