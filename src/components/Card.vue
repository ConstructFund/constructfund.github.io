<template>
  <v-card class="child">
    <v-toolbar
      style="padding-left: 15px; padding-right: 15px"
      :color="content.hasWebsite ? 'primary' : ''"
    >
      <h2>{{ content.name }}</h2>
      <v-spacer></v-spacer>
      <div v-if="content.hasWebsite">
        <v-btn @click="openWebsite" text> Open Website </v-btn>
        <v-icon right>mdi-open-in-new</v-icon>
      </div>
    </v-toolbar>
    <v-card-text>
      {{ content.description }}
    </v-card-text>
    <v-card-actions>
      <div>
        <v-chip :color="chipColor">
          <div class="prechip">Status:</div>
          {{ content.status }}
        </v-chip>
      </div>
      <div>
        <v-btn @click="openRepo">Open Repo</v-btn>
        <v-icon>mdi-github</v-icon>
      </div>
    </v-card-actions>
  </v-card>
</template>

<script setup>
import { computed } from "vue";

// define prop for content object
const props = defineProps({
  content: Object,
});

const chipColor = computed(() => {
  return {
    "In Development": "success",
    Maintenance: "warning",
    "On Hiatus": "warning",
    Abandonned: "error",
    Shipped: "info",
  }[props.content.status];
});

function openWebsite() {
  window.open(props.content.url);
}

function openRepo() {
  window.open(props.content.repo);
}
</script>

<style scoped>
.child {
  margin-top: 20px;
  margin-bottom: 20px;
  width: 100%;
}

.prechip {
  background-color: rgb(var(--v-theme-primary)) !important;
  height: 100%;
  margin-left: -12px;
  text-align: center;
  padding-left: 12px;
  padding-right: 4px;
  margin-right: 6px;
  border-top-left-radius: 100px;
  border-bottom-left-radius: 100px;
  align-items: center;
  display: flex;
  color: white;
}
</style>
