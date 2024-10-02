<template>
  <nav class="fixed w-full z-10">
    <Disclosure
      as="div"
      class="dark:bg-slate-900/50 backdrop-blur-xl bg-slate-50/50"
      v-slot="{ open }"
    >
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="flex h-16 items-center justify-between">
          <div class="flex items-center">
            <div class="flex-shrink-0">
              <h1 class="font-bold text-black dark:text-white">PCV-AI</h1>
            </div>
          </div>
          <div class="">
            <div class="ml-4 flex items-center md:ml-6">
              <button
                id="btn-dark"
                @click="handleTheme"
                type="button"
                class="relative rounded-full bg-slate-200 dark:bg-slate-800 p-1 dark:text-gray-400 text-gray-600 dark:hover:text-white hover:text-black focus:outline-none focus:ring-2 dark:focus:ring-white focus:ring-black focus:ring-offset-2 dark:focus:ring-offset-gray-800 focus:ring-offset-gray-200"
              >
                <span class="absolute -inset-1.5" />
                <span class="sr-only">View notifications</span>
                <SunIcon
                  v-if="colorMode.value == 'dark'"
                  class="h-6 w-6"
                  aria-hidden="true"
                />
                <MoonIcon
                  v-if="colorMode.value == 'light'"
                  class="h-6 w-6"
                  aria-hidden="true"
                />
              </button>
            </div>
          </div>
        </div>
      </div>

      <DisclosurePanel class="md:hidden">
        <div class="space-y-1 px-2 pb-3 pt-2 sm:px-3">
          <!-- <DisclosureButton
            v-for="item in navigation"
            :key="item.name"
            as="a"
            :href="item.href"
            :class="[
              item.current
                ? 'bg-gray-900 text-white'
                : 'text-gray-300 hover:bg-gray-700 hover:text-white',
              'block rounded-md px-3 py-2 text-base font-medium',
            ]"
            :aria-current="item.current ? 'page' : undefined"
            >{{ item.name }}</DisclosureButton
          > -->
        </div>
        <div class="border-t border-gray-700 pb-3 pt-4">
          <div class="flex items-center px-5">
            <button
              id="btn-dark"
              @click="handleTheme"
              type="button"
              class="relative rounded-full bg-gray-800 p-1 text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800"
            >
              <span class="absolute -inset-1.5" />
              <span class="sr-only">View notifications</span>
              <SunIcon
                v-if="colorMode.value == 'dark'"
                class="h-6 w-6"
                aria-hidden="true"
              />
              <MoonIcon
                v-if="colorMode.value == 'light'"
                class="h-6 w-6"
                aria-hidden="true"
              />
            </button>
          </div>
        </div>
      </DisclosurePanel>
    </Disclosure>
  </nav>
</template>

<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from "@headlessui/vue";
import {
  Bars3Icon,
  XMarkIcon,
  SunIcon,
  MoonIcon,
} from "@heroicons/vue/24/outline";

const colorMode = useColorMode();

const navigation = [
  { name: "Dashboard", href: "#", current: true },
  { name: "Team", href: "#", current: false },
  { name: "Projects", href: "#", current: false },
  { name: "Calendar", href: "#", current: false },
  { name: "Reports", href: "#", current: false },
];

const handleTheme = () => {
  console.log("oli");
  if (colorMode.value == "dark") colorMode.preference = "light";
  else colorMode.preference = "dark";
};
</script>
