<template>
  <div class="bg-slate-200 dark:bg-slate-950 w-screen auto overflow-scroll">
    <client-only>
      <Navbar />
      <main class="min-h-full">
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
// SEO
useHead({
  title: "PCV-AI",
  meta: [
    {
      name: "Para Cego Ver com AI",
      content:
        "Geração de alt-text com o modelo Gemini Flash 1.5 para obras de arte latino americanas disponíveis na Wikimedia.",
    },
  ],
  bodyAttrs: {
    class: "test",
  },
  script: [{ innerHTML: "console.log('Hello world')" }],
});
</script>

<style>
body {
  background-color: #e2e8f0;
}
.dark-mode body {
  background-color: #020617;
}
</style>
