<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-col class="d-flex justify-space-around">
        <v-toolbar-title class="white--text">VUE TREE</v-toolbar-title>
      </v-col>
    </v-app-bar>

    <v-main>
      <h1>{{ this.content }}</h1>
      <Tree :node="root" @onClick="nodeWasClicked"></Tree
    ></v-main>
  </v-app>
</template>

<script>
import Tree from "./components/Tree";
import root from "./data.json";
export default {
  name: "App",

  components: { Tree },
  methods: {
    nodeWasClicked(node) {
      this.content = node.name;
    },
  },

  data: () => ({
    content: "",
    root,
  }),
};
</script>


<style>
body {
  background-color: #333;
  color: white;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>