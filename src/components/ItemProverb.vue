<script setup>
const props = defineProps({ proverb: String, meaning: String, lang: String })
</script>

<template>
  <div class="proverb">
    <div class="proverb__item">{{ proverb }}</div>
    <div>{{ meaning }}</div>
    <div class="proverb__lang">( {{ lang }} )</div>
  </div>
</template>

<style class="postcss">
.proverb {
  display: flex;
}

.proverb__item {
  font-weight: bold;
}

.proverb__lang {
  font-style: italic;
}

.proverb div {
  margin: 0.5rem;
}
</style>
