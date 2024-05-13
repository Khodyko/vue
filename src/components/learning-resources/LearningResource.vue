<script setup>
import { defineProps } from 'vue';

defineProps({
  title: { type: String },
  description: { type: String },
  link: { type: String },
});
</script>

<template>
  <li>
    <BaseCard>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat">Delete</base-button>
      </header>
      <p>{{ description }}</p>
      <a :href="link">View resource</a>
    </BaseCard>
  </li>
</template>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>
