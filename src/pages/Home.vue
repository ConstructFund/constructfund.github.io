<template>
  <v-toolbar app>
    <v-toolbar-title>Construct Fund</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn text :href="issueURL">
      <v-icon start>mdi-open-in-new</v-icon>
      Report issue
    </v-btn>
  </v-toolbar>
  <div class="parent">
    <Card v-for="(item, i) in content" :key="i" :content="item"/>
  </div>
</template>

<script setup>
import Card from "@/components/Card.vue";
import content from "@/assets/content.json";

const issueURL = "https://github.com/ConstructFund/constructfund.github.io/issues/"
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

/* media query for mobile padding */
@media (max-width: 700px) {
  .parent {
    padding-left: 20px;
    padding-right: 20px;
  }
}

/* media query for small screen padding min width 801 */
@media (min-width: 701px) and (max-width: 1200px) {
  .parent {
    padding-left: 10%;
    padding-right: 10%;
  }
}

/* media query for small screen padding min width 801 */
@media (min-width: 1201px) and (max-width: 1500px) {
  .parent {
    padding-left: 20%;
    padding-right: 20%;
  }
}
</style>