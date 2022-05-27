<template>
  <el-container style="height: 100%">
    <el-aside width="auto" height="100%">
      <common-aside></common-aside>
    </el-aside>
    <el-container>
      <el-header>
        <common-header></common-header>
      </el-header>
      <el-main>
        <router-view />
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
import CommonHeader from "../components/CommonHeader.vue";
import CommonAside from "../components/CommonAside.vue";

export default {
  name: "Main",
  components: { CommonAside, CommonHeader, CommonTag },
};
</script>