<template>
  <div class="menu-tree">
    <div class="label-wrapper row" @click="toggleChildren">
      <div :style="indent()">
        <p class="text-start">
          <span v-if="nodes.children.length > 0">
            {{this.iconGet()}}
          </span>
          {{ label }}
          <b-badge style="background-color:#e5001c">
            {{ nodes.discoveredIssues }}
          </b-badge>
          <span style="color: #e5001c; font-size: smaller">
            {{ this.childrenIssuesCount }}
          </span>
          <span>

          </span>
        </p>
      </div>
    </div>

    <div v-if="showChildren">
      <menu-tree
          :depth="depth + 1"
          v-for="node in nodes.children"
          :key="node.id"
          :label="node.name"
          :nodes="node"
      >
      </menu-tree>
    </div>
  </div>
</template>

<script>
import MenuTree from './MenuTree.vue'

export default {
  name: "MenuTree",
  components: {
    MenuTree,
  },
  props: ['nodes', 'label', 'depth'],
  data() {
    return {
      showChildren: false,
      childrenIssuesCount: 0
    }
  },
  mounted() {
    this.childrenIssuesCount = 0
    this.sumIssues()
  },
  methods: {
    toggleChildren() {
      this.showChildren = !this.showChildren
    },
    indent() {
      return 'transform: translate(' + this.depth * 50 + 'px)'
    },
    iconGet() {
      return this.showChildren ? '-' : '+'
    },
    sumIssues() {
        this.childrenIssuesCount = this.nodes.children.reduce(function recur(sum, child) {
        return sum + (child.total = (child.children ?? []).reduce(recur, child.discoveredIssues));
      }, 0);
    }
  }
}
</script>

<style scoped>

</style>