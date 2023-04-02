<template>
  <v-container fluid>
    <section id="home">
      <v-row
        dense
        justify="center"
        align="center"
        style="min-height: calc(100vh - 88px)"
      >
        <v-container>
          <v-row>
            <v-col class="text-center text-md-right" cols="12" md="5" lg="4">
              <v-avatar size="300px" style="border: 5px solid #616161">
                <v-img src="/assets/img/me.jpg" alt="Deyvid Holz" />
              </v-avatar>
            </v-col>

            <v-col class="text-center text-md-left">
              <h1>Deyvid Holz</h1>

              <v-row justify="space-between" class="text-grey">
                <v-col>Software Engineer</v-col>
                <v-col>23 years old</v-col>
                <v-col>Brazil</v-col>
              </v-row>

              <v-divider class="my-2" />

              <p class="text-justify">
                I have been passionate about technology since 13, starting with
                learning Java to create Minecraft servers. My interest grew with
                web development, and now my main goal is to be an exceptional
                developer, focusing on good practices and understanding the
                reasons behind codes and frameworks.

                <br />
                <br />

                I'm committed to continuous improvement, studying not only new
                technologies but also mathematics, algorithms, programming
                languages, and clean code principles.
              </p>
            </v-col>
          </v-row>
        </v-container>
      </v-row>
    </section>

    <section id="skills" class="mb-12">
      <v-container>
        <h2 class="text-h4">Skills</h2>
        <v-divider class="my-4" />
        <skills :data="skills" />
      </v-container>
    </section>

    <section id="projects">
      <v-container>
        <h2 class="text-h4">Projects</h2>
        <v-divider class="my-4" />
        <projects :data="projects" />
      </v-container>
    </section>
  </v-container>

  <v-card flat class="px-12 py-4 text-center" rounded="0">
    <v-btn
      flat
      icon="mdi-linkedin"
      size="x-large"
      :href="contact.linkedin"
      target="_blank"
    />

    <v-btn
      flat
      icon="mdi-github"
      size="x-large"
      :href="contact.github"
      target="_blank"
    />

    <v-btn
      flat
      icon="mdi-email"
      size="x-large"
      :href="contact.email"
      target="_blank"
    />

    <v-dialog v-model="dialogs.joke.show" width="420px">
      <v-card>
        <v-card-text>
          {{ joke }}
        </v-card-text>

        <v-card-actions>
          <v-btn color="primary" block @click="dialogs.joke.show = false">
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <div @click="showSomethingCool" style="cursor: pointer">
      Copyright &copy; 202... Okay, there's no copyright. But you can click here
      to see something cool!
    </div>
  </v-card>

  <dialog :model-value="dialogs.joke.show" />
</template>

<script lang="ts">
import Skills from "./components/skills.vue";
import Projects from "./components/projects.vue";

export default {
  components: { Skills, Projects },

  data: () => ({
    joke: "",

    contact: {
      linkedin: "https://www.linkedin.com/in/deyvidholz/",
      github: "https://github.com/DeyvidHolz",
      email: "mailto:deyvidholzt@gmail.com",
    },

    skills: [
      {
        title: "JavaScript",
        value: 100,
        color: "yellow-darken-2",
        icon: "mdi-language-javascript",
      },
      {
        title: "PHP",
        value: 100,
        color: "indigo-accent-2",
        icon: "mdi-language-php",
      },
      {
        title: "C#",
        value: 80,
        color: "deep-purple-accent-2",
        icon: "mdi-language-csharp",
      },
      { title: "Java", value: 20, color: "red", icon: "mdi-language-java" },

      {
        title: "TypeScript",
        value: 100,
        color: "blue",
        icon: "mdi-language-typescript",
      },
      {
        title: "NodeJS",
        value: 100,
        color: "green-darken-1",
        icon: "mdi-nodejs",
      },
      {
        title: "VueJS",
        value: 100,
        color: "teal-accent-4",
        icon: "mdi-vuejs",
      },
      { title: "Unity", value: 15, color: "grey-lighten-1", icon: "mdi-unity" },
      {
        title: "Laravel",
        value: 100,
        color: "red-darken-2",
        icon: "mdi-laravel",
      },
      { title: "NestJS", value: 70, color: "red-darken-2" },
      { title: "AdonisJS", value: 90, color: "grey-lighten-1" },

      { title: "Postgres", value: 100, color: "blue", icon: "mdi-database" },
      {
        title: "MongoDB",
        value: 100,
        color: "green-lighten-1",
        icon: "mdi-database",
      },
      {
        title: "MySQL / MariaDB",
        value: 100,
        color: "blue",
        icon: "mdi-database",
      },

      { title: "Puppeteer", value: 100, color: "grey-lighten-1" },
      {
        title: "Vuetify",
        value: 100,
        color: "blue",
        icon: "mdi-vuetify",
      },
      { title: "Express", value: 100, color: "grey-lighten-1" },
      { title: "TypeORM", value: 100, color: "blue" },
      { title: "Sequelize", value: 100, color: "yellow-darken-2" },
      {
        title: "ESLint",
        value: 100,
        color: "deep-purple-lighten-2",
        icon: "mdi-eslint",
      },
      { title: "Jest", value: 100, color: "deep-orange-darken-2" },
      { title: "Packagist", value: 85, color: "orange" },
      { title: "NPM", value: 100, color: "orange", icon: "mdi-npm" },
      { title: "Yarn", value: 100, color: "blue" },

      { title: "Git", value: 100, color: "orange" },
      { title: "Docker", value: 100, color: "blue", icon: "mdi-docker" },
      { title: "GraphQL", value: 70, color: "purple", icon: "mdi-graphql" },
      { title: "Swagger", value: 100, color: "green-lighten-1" },
      {
        title: "Digital Ocean",
        value: 70,
        color: "blue",
        icon: "mdi-digital-ocean",
      },
      { title: "AWS", value: 50, color: "orange", icon: "mdi-aws" },

      {
        title: "Github",
        value: 100,
        color: "grey-lighten-1",
        icon: "mdi-github",
      },
      { title: "BitBucket", value: 100, color: "blue", icon: "mdi-bitbucket" },
      {
        title: "GitLab",
        value: 100,
        color: "orange-darken-1",
        icon: "mdi-gitlab",
      },
      { title: "Figma", value: 70, color: "red" },
    ],

    projects: [
      {
        title: "Age of Wars",
        description:
          "Multiplayer Strategy game with more than 100 countries available",
        images: ["/aow/1.png", "/aow/2.png", "/aow/3.png"],
        stack: [
          "NodeJS",
          "TypeScript",
          "JavaScript",
          "VueJS",
          "Vuetify",
          "Socket.io",
          "Postgres",
          "TypeORM",
          "Docker",
        ],
        previewUrl: "https://github.com/deyvidholz/age-of-wars-frontend",
      },
      {
        title: "Memorizer",
        description:
          "Simple app to help you memorize words from other languages",
        images: ["/memorizer/1.png", "/memorizer/2.png", "/memorizer/3.png"],
        stack: ["Vue", "Vuetify"],
        previewUrl: "https://github.com/deyvidholz/memorizer-vue",
      },
      {
        title: "HarpiaJS",
        description:
          "Project Boilerplate with  express, typeorm, jest, docker and other essential modules.",
        stack: ["NodeJS", "TypeScript", "Postgres", "TypeORM", "Docker"],
        previewUrl: "https://github.com/deyvidholz/harpia-nodejs",
        // productionUrl: "https://github.com/deyvidholz/harpia-nodejs",
      },

      {
        title: "NestJS JWT Auth",
        description: "Simple project with JWT Authentication.",
        stack: ["NodeJS", "TypeScript", "NestJS", "Jest"],
        previewUrl: "https://github.com/deyvidholz/nestjs-jwt",
      },
      {
        title: "7D2D - Better Config",
        description:
          "Take your 7 Days to Die gameplay to the next level with zombie headshots, modified item damage, and more! Last tested on Alpha 20.3",
        stack: ["NodeJS"],
        previewUrl: "https://github.com/deyvidholz/7D2DBetterConfig",
      },
    ],

    funniestJokesOfTheCentury: [
      "Why do programmers prefer dark mode? Because light attracts bugs.",
      "Why did the programmer quit his job? He didn't get arrays.",
      "Why did the programmer go broke? He used up all his cache.",
      "Why did the SQL query go to therapy? It had a lot of inner joins.",
      "Why do programmers hate nature? There's too many bugs.",
      "Why do programmers always mix up Halloween and Christmas? Because Oct 31 equals Dec 25.",
      "Why do programmers prefer dogs to cats? Because dogs have a main() function.",
      "Why do programmers always mix up Christmas and Halloween? Because Oct 31 equals Dec 25.",
      "Why do Java developers wear glasses? Because they can't C#.",
      "Why do programmers prefer dark chocolate? Because it's semisweet.",
    ],

    dialogs: {
      joke: {
        show: false,
      },
    },
  }),

  methods: {
    showSomethingCool() {
      const randomIndex = Math.floor(
        Math.random() * this.funniestJokesOfTheCentury.length
      );

      this.joke = this.funniestJokesOfTheCentury[randomIndex];
      this.dialogs.joke.show = true;
    },
  },
};
</script>
