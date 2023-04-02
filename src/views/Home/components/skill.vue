<template>
  <div class="d-flex align-center">
    <v-icon class="mr-1" :color="iconColor || color">
      {{ icon }}
    </v-icon>
    <h3 v-html="title" class="text-button" />
  </div>

  <v-progress-linear :model-value="value" :color="color" height="15" striped />
</template>

<script lang="ts">
export type Skill = {
  title: string;
  icon?: string;
  color?: string;
  iconColor?: string;
  value?: string | number;
};

export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
      default: "mdi-code-braces",
    },
    color: {
      type: String,
      default: "indigo-accent-2",
    },
    iconColor: {
      type: String,
      default: null,
    },
    value: {
      type: [Number, String],
      default: 100,
    },
  },
};
</script>
