<template>
  <v-row>
    <v-col cols="12" md="4" lg="3" v-for="(skill, index) in data" :key="index">
      <skill
        :title="skill.title"
        :value="skill.value"
        :color="skill.color"
        :icon="skill.icon"
      />
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { PropType } from "vue";
import skill, { Skill } from "./skill.vue";

export default {
  components: { skill },

  props: {
    data: {
      type: Array as PropType<Skill[]>,
      required: true,
    },
  },
};
</script>
