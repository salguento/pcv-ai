<template>
  <div class="bg-white-100 dark:bg-slate-950">
    <Navbar />
    <Card :artworks="content.body" />
  </div>
</template>

<script setup>
const content = await queryContent("/alt_text").findOne();
console.log(content.body[1]);
</script>
