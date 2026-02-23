<script setup lang="ts">
import type { NavigateBar } from '@nuxt/ui'
import type { NavigateFooter } from '@nuxt/ui'

const route = useRoute()

const items = computed<NavigateBar[]>(() => [
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
  },
  {
    label: 'Profile',
    to: '/profile',
    icon: 'i-lucide-user',
    active: route.path === '/profile'
  },
  {
    label: 'Logout',
    to: '/logout',
    icon: 'i-lucide-log-out',
    active: route.path === '/logout'
  }
])

const menus = computed<NavigateFooter[]>(() => [
  {
    label: 'About',
    to: '/about'
  },
  {
    label: 'Contact',
    to: '/contact'
  },
  {
    label: 'Privacy Policy',
    to: '/privacy-policy'
  },
  {
    label: 'Terms of Service',
    to: '/terms-of-service'
  }
])
</script>

<template>
  <UApp class="w-fullscreen">
    <UHeader class="text-center font-bold text-lg">
      <UNavigationMenu :items="items" />
      <UInput type="file"/>
    </UHeader>
    <UMain />
    <UFooter>
      <UNavigationMenu :items="menus"/>
    </UFooter>
  </UApp>
</template>
