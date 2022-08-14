<template>
  <div>
    <div class="container">
      <div class="row justify-content-center">
        <b-card class="w-50" style="background-color:#f7f7f7;">
          <div v-if="showChildren">
              <menu-tree
                  v-for="item in items.resultDetails"
                  :key="item.id"
                  :nodes="item"
                  :label="item.name"
                  :depth="0"
              >
              </menu-tree>
          </div>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
import MenuTree from "@/components/MenuTree";
import TreeItems from '../assets/tree.json'

export default {
  name: 'InventoryTree',
  components: {MenuTree},
  data(){
    return {
      showChildren:true,
      items: TreeItems
    }
  },
}
</script>

<style scoped>

</style>
