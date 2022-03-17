<script setup>
import { ref } from 'vue'
import fauna from 'faunadb'
import ItemProverb from './ItemProverb.vue'

const item = ref(null)

const q = fauna.query
const client = new fauna.Client({
  secret: 'fnAEh6lECJACTIYijNSPtBYVbQbxPYz5LuOcEmqf',
  domain: 'db.fauna.com' // Adjust if you are using Region Groups
})

client
  .query(q.Get(q.Ref(q.Collection('proverbs'), '326407254705177164')))
  .then((res) => {
    item.value = res.data
  })
  .catch((err) =>
    console.error(
      'Error: [%s] %s %s',
      err.name,
      err.message,
      err.errors()[0].description
    )
  )
</script>

<template>
  <h2>Home</h2>

  <div>
    <h1>Proverbs</h1>
    <ItemProverb
      :proverb="item.proverb"
      :meaning="item.meaning"
      :lang="item.lang"
    />
  </div>
</template>
