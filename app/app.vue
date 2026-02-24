<script setup lang="ts">
import type { NavigateBar, NavigateFooter, NavigateMain } from '@nuxt/ui'
import tailwindcss from '@tailwindcss/vite'

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

const main = computed<NavigateMain[]>(() => [
  {
    label: 'Dashboard',
    to: '/dashboard',
    icon: 'i-lucide-layout-dashboard',
    active: route.path === '/dashboard'
  },
  {
    label: 'Tasks',
    to: '/tasks',
    icon: 'i-lucide-list-check',
    active: route.path === '/tasks'
  },
  {
    label: 'Calendar',
    to: '/calendar',
    icon: 'i-lucide-calendar',
    active: route.path === '/calendar'
  },
  {
    label: 'Analytics',
    to: '/analytics',
    icon: 'i-lucide-bar-chart-2',
    active: route.path === '/analytics'
  },
  {
    label: 'Team',
    to: '/team',
    icon: 'i-lucide-users',
    active: route.path === '/team'
  },
  {
    label: 'Settings',
    to: '/settings',
    icon: 'i-lucide-settings',
    active: route.path === '/settings'
  },
  {
    label:'Help',
    to: '/help',
    icon: 'i-lucide-help-circle',
    active: route.path === '/help'
  },
  {
    label: 'Logout',
    to: '/logout',
    icon: 'i-lucide-log-out',
    active: route.path === '/logout'
  }
])
</script>

<template>
  <UApp>
    <UHeader class="text-center font-bold text-lg bg-gray-950 text-white">
      <UNavigationMenu :items="items" class="w-fullscreen " />
      <UInput type="file"/>
    </UHeader>
    <UMain>
      <div class ="flex gap-4">
          <UNavigationMenu orientation="vertical" :items="main" class="text-2xl text-black p-5 " />
      </div>
    </UMain>
    <UFooter class="bg-gray-950">
      <UNavigationMenu :items="menus" />
    </UFooter>
  </UApp>
</template>
