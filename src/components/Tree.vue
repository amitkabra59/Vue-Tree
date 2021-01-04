<template>
  <div>
    <div
      @click="nodeClicked"
      :style="{ 'margin-left': `${indent * 20}px` }"
      class="node"
    >
      <span v-if="hasChildNodes" class="type">{{
        expanded ? "&#9660;" : "&#9658;"
      }}</span>
      <span class="type" v-else>&#9671;</span>
      {{ node.name }}
    </div>
    <v-template v-if="expanded">
      <Tree
        v-for="child in node.nodes"
        :key="child.name"
        :node="child"
        :indent="indent + 1"
        @onClick="(node) => $emit('onClick', node)"
      />
    </v-template>
  </div>
</template>
<script>
export default {
  name: "Tree",
  props: {
    node: Object,
    indent: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      expanded: false,
    };
  },
  methods: {
    nodeClicked() {
      this.expanded = !this.expanded;
      if (!this.hasChildren) {
        this.$emit("onClick", this.node);
      }
    },
  },
  computed: {
    hasChildNodes() {
      return this.node.nodes;
    },
  },
};
</script>

<style scoped>
.node {
  text-align: left;
  font-size: 18px;
}
.type {
  margin-right: 10px;
}
</style>