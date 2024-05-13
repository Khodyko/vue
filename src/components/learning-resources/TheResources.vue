<!-- eslint-disable -->
<script setup>
import { defineProps, ref, provide, defineAsyncComponent, computed } from 'vue';
import StoredResources from './StoredResources.vue';
import AddResources from './AddResources.vue';

const selectedTab = ref('stored-resources');
const resources = ref([
  {
    id: 'official-guide',
    title: 'OfficialGuide',
    description: 'The official Vue.js focus',
    link: 'https://vuejs.org',
  },
  {
    id: 'google',
    title: 'Google data',
    description: 'Googling is everything',
    link: 'https://google.com',
  },
]);

const storedBtnTab = computed(() => {
  return selectedTab.value === 'stored-resources' ? null : 'flat';
});

const addBtnTab = computed(() => {
  return selectedTab.value === 'add-resources' ? null : 'flat';
});

provide('resources', resources.value);

function setTab(type) {
  selectedTab.value = type;
}
</script>

<template>
  <BaseCard>
    <BaseButton @click="setTab('stored-resources')" :mode="storedBtnTab"
      >Stored Resources</BaseButton
    >
    <BaseButton @click="setTab('add-resources')" :mode="addBtnTab"
      >Add Resources</BaseButton
    >
  </BaseCard>
  <StoredResources v-if="selectedTab == 'stored-resources'" />
  <AddResources v-else />
</template>
