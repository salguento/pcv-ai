<template>
  <div class="bg-slate-200 dark:bg-slate-950">
    <client-only>
      <Navbar />
      <main>
        <div class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
          <Hero />
          <Card :artworks="content.body" />
        </div>
      </main>
      <Footer />
    </client-only>
  </div>
</template>

<script setup>
const content = await queryContent("/alt_text").findOne();

function shuffle(a) {
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}

shuffle(content.body);
</script>
