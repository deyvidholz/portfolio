<template>
  <v-card class="mx-auto" max-width="344">
    <v-img
      :src="baseURL + (images[0] as string)"
      height="200px"
      cover
      v-if="images?.length === 1"
    />

    <v-carousel
      v-else-if="images?.length"
      height="200px"
      hide-delimiter-background
      show-arrows="hover"
      cycle
    >
      <v-carousel-item
        :src="baseURL + image"
        cover
        :key="index"
        v-for="(image, index) in images"
      />
    </v-carousel>

    <v-img
      src="/assets/img/projects/no-image.jpg"
      height="200px"
      cover
      v-else
    />

    <v-card-title class="text-orange">
      {{ title }}
    </v-card-title>

    <v-card-text class="text-grey-lighten-1" style="min-height: 100px">
      <span v-html="description"></span>
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="orange-accent-1"
        variant="text"
        :href="productionUrl"
        target="_blank"
        v-if="productionUrl"
      >
        <v-icon class="mr-1">mdi-rocket</v-icon>
        Play
      </v-btn>

      <v-btn
        color="indigo-accent-1"
        variant="text"
        :href="previewUrl"
        target="_blank"
        v-if="previewUrl"
      >
        <v-icon class="mr-1">mdi-source-repository</v-icon>
        Explore
      </v-btn>

      <v-spacer />

      <v-btn
        :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        @click="show = !show"
      />
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider />

        <v-card-text>
          <span class="text-orange"><b>Stack:</b></span>
          <br />
          {{ stack?.join(", ") }}
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script lang="ts">
import { PropType } from "vue";

export type Project = {
  title: string;
  description?: string;
  images?: any[];
  stack?: string[];
  previewUrl?: string;
  productionUrl?: string;
};

export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
    },
    images: {
      type: Array,
    },
    stack: {
      type: Array as PropType<string[]>,
    },
    previewUrl: {
      type: String,
    },
    productionUrl: {
      type: String,
    },
  },

  data: () => ({
    show: false,
    baseURL: "/assets/img/projects",
  }),
};
</script>
