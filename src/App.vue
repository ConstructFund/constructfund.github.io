<template>
  <v-app dark>
    <v-main>
      <v-toolbar app>
        <v-toolbar-title>Construct Fund</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn text @click="reportIssue()">
          <v-icon right>mdi-open-in-new</v-icon>
          Report issue
        </v-btn>
      </v-toolbar>
      <div class="parent">
        <Card v-for="(item, i) in content" key="i" :content="item" />
      </div>
    </v-main>
  </v-app>
</template>

<script setup>
import Card from "@/components/Card.vue";
import content from "@/assets/content.json";

function reportIssue() {
  window.open("https://github.com/ConstructFund/color-addon-generator/issues/");
}
</script>

<style scoped>
.parent {
  width: 100%;
  height: calc(100% - 64px);
  overflow: auto;
  padding-left: 30%;
  padding-right: 30%;
  padding-top: 50px;
  padding-bottom: 50px;
}
</style>
