<template>
  <header class="">
    <div class="mx-auto max-w-2xl py-12 md:py-24 lg:py-32">
      <div class="hidden sm:mb-8 sm:flex sm:justify-center">
        <div
          class="relative rounded-full px-3 py-1 text-sm leading-6 text-gray-600 ring-1 ring-gray-900/10 dark:text-gray-400 dark:ring-gray-100/10"
        >
          Projeto de Extensão Universitária do curso de Análise e
          Desenvolvimento de Sistemas - UNITER
        </div>
      </div>
      <div class="text-center">
        <h1
          class="text-balance text-4xl font-bold tracking-tight text-gray-900 dark:text-gray-100 sm:text-6xl"
        >
          Para Cego Ver com AI
        </h1>
        <p class="mt-6 text-lg leading-8 text-gray-600 dark:text-gray-400">
          Geração de <em>alt-text</em> com o modelo
          <em>Gemini Flash 1.5</em> para obras de arte latino americanas
          disponíveis na <em>Wikimedia</em>.
        </p>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";
import { Dialog, DialogPanel } from "@headlessui/vue";
import { Bars3Icon, XMarkIcon } from "@heroicons/vue/24/outline";

const navigation = [
  { name: "Product", href: "#" },
  { name: "Features", href: "#" },
  { name: "Marketplace", href: "#" },
  { name: "Company", href: "#" },
];

const mobileMenuOpen = ref(false);
</script>
