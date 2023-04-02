<template>
  <v-navigation-drawer
    v-model="drawer"
    app
    mobile-break-point="960"
    location="right"
    temporary
  >
    <v-list>
      <v-list-item v-for="(item, index) in items" :key="index">
        <v-list-item-title>
          <v-btn :color="item.color" @click="scrollTo">
            <v-icon class="mr-1">{{ item.icon }}</v-icon>
            {{ item.text }}
          </v-btn>
        </v-list-item-title>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>

  <v-app-bar app color="grey-darken-4">
    <template v-slot:prepend v-if="$vuetify.display.smAndDown"> </template>

    <v-app-bar-title
      class="text-blue font-weight-bold"
      style="cursor: pointer"
      @click="scrollToTop"
    >
      Deyvid Holz
    </v-app-bar-title>

    <template v-slot:append>
      <div v-if="$vuetify.display.mdAndUp">
        <v-btn
          :color="item.color"
          :key="index"
          v-for="(item, index) in items"
          @click="scrollTo(item.link)"
        >
          <v-icon class="mr-1">{{ item.icon || "mdi-code-braces" }}</v-icon>
          {{ item.text }}
        </v-btn>
      </div>

      <v-app-bar-nav-icon @click="drawer = !drawer" v-else />
    </template>
  </v-app-bar>
</template>

<script lang="ts">
export default {
  data: () => ({
    drawer: false,
    items: [
      { text: "Skills", icon: "mdi-code-braces", link: "#skills", color: "" },
      {
        text: "Projects",
        icon: "mdi-folder-multiple",
        link: "#projects",
        color: "",
      },
    ],
  }),

  computed: {
    currentScrollPosition() {
      return window.pageYOffset || document.documentElement.scrollTop;
    },
  },

  methods: {
    scrollToTop() {
      window.scrollTo({
        top: 0,
        left: 0,
        behavior: "smooth",
      });
    },

    scrollTo(selector: string) {
      const element: HTMLElement | null = document.querySelector(selector);

      if (element) {
        const elementPosition = element.offsetTop;
        window.scrollTo({ top: elementPosition - 40, behavior: "smooth" });
      }
    },
  },
};
</script>
