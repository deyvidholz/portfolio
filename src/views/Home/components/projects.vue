<template>
  <v-row>
    <v-col cols="12" md="4" v-for="(project, index) in data" :key="index">
      <project
        :title="project.title"
        :description="project.description"
        :images="project.images"
        :stack="project.stack"
        :preview-url="project.previewUrl"
        :production-url="project.productionUrl"
      />
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { PropType } from "vue";
import project, { Project } from "./project.vue";

export default {
  components: { project },

  props: {
    data: {
      type: Array as PropType<Project[]>,
      required: true,
    },
  },
};
</script>
