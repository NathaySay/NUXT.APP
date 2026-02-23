<script setup lang="ts">
  import type {NavigateBar} from "@nuxt/ui";

  const route = useRoute();

  const items = computed<NavigateBar[]>(() =>[
    {
      label: 'Home',
      to: '/',
      icon: 'i-lucide-home',
      active: route.path === '/'
    },
    {
      label: 'Dashboard',
      to: '/dashboard',
      icon: 'i-lucide-layout-dashboard',
      active: route.path === '/dashboard'
    },
    {
      label: 'Settings',
      to: '/settings',
      icon: 'i-lucide-settings',
      active: route.path === '/settings'
    }
  ])
</script>

<template>
  <UApp>
    <UHeader>
      <UNavigationMenu :items="items" />
    </UHeader>
    <UMain></UMain>
    <UFooter></UFooter>
  </UApp>
</template>
