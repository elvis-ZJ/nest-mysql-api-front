<template>
  <el-submenu v-if="item.children && item.children.length" :index="item.url">
    <template slot="title">
      <i v-if="item.icon" :class="item.icon"></i>
      <i v-else class="el-icon-folder-opened"></i>
      <span slot="title">
        {{ item.name }}
      </span>
    </template>
    <!-- 递归使用该组件 -->
    <template v-for="(m, i) in item.children">
      <MenuItem :item="m" :key="i" />
    </template>
  </el-submenu>
  <el-menu-item v-else :index="item.url">
    <i v-if="item.icon" :class="item.icon"></i>
    <i v-else class="el-icon-tickets"></i>
    <span slot="title">{{ item.name }}</span>
  </el-menu-item>
</template>

<script>

export default {
  name: 'MenuItem',
  props: {
    item: Object,
    default: () => { },
  }
}
</script>

<style scoped lang="scss">
/* .router {
  color: #e5e5e5;
  text-decoration: none;
}
.active {
  color: #f00;
} */
</style>
