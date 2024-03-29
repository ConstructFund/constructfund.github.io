<template>
  <v-card class="child">
    <v-toolbar
      style="padding-left: 15px; padding-right: 15px"
      :color="content.hasWebsite ? 'primary' : ''"
      v-if="!isMobile"
    >
      <h2 class="title">{{ content.name }}</h2>
      <v-spacer></v-spacer>
      <div v-if="content.hasWebsite">
        <v-btn
            :href="props.content.url"
            variant="text">
            Open Website
            <v-icon end>mdi-open-in-new</v-icon>
          </v-btn>
      </div>
    </v-toolbar>
    <div v-else>
      <v-sheet
        width="100%"
        style="
          padding-left: 15px;
          padding-right: 15px;
          flex-direction: row;
          display: flex;
          align-items: center;
        "
        :color="content.hasWebsite ? 'primary' : 'rgba(255, 255, 255, 0.1)'"
      >
        <h2 class="title">{{ content.name }}</h2>
        <v-spacer></v-spacer>
        <v-icon v-if="content.hasWebsite" right>mdi-open-in-new</v-icon>
      </v-sheet>

      <v-sheet v-if="content.hasWebsite" width="100%" class="button">
        <v-btn :href="props.content.url" variant="text" style="width: 100%">
          Open Website
        </v-btn>
      </v-sheet>
    </div>
    <v-card-text>
      {{ content.description }}
    </v-card-text>
    <v-card-actions>
      <div>
        <v-chip :color="chipColor">
          <div class="prechip">Status</div>
          {{ content.status }}
        </v-chip>
      </div>
      <div style="display: flex; flex-wrap: nowrap" v-if="content.hasRepo">
        <v-btn :href="props.content.repo">
          Open Repo
          <v-icon end>mdi-github</v-icon>
        </v-btn>
      </div>
    </v-card-actions>
  </v-card>
</template>

<script setup>
import { computed } from "vue";
import { useMediaQuery } from "@vueuse/core";

// define prop for content object
const props = defineProps({
  content: Object,
});

const chipColor = computed(() => {
  return {
    "In Development": "success",
    Maintenance: "warning",
    "On Hiatus": "warning",
    Legacy: "error",
    Shipped: "info",
  }[props.content.status];
});

const isMobile = useMediaQuery("(max-width: 700px)");
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

.button {
  width: 100%;
  /* linear gradient to white */
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.1) 100%
  );
}
</style>
