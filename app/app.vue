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
    active: true
  },
  {
    label: 'Tasks',
    to: '/tasks',
    icon: 'i-lucide-list-check',
    active: route.path === '/tasks',
    defaultOpen: false,
    children: [
      {
        label: 'My Tasks',
        to: '/tasks/my',
        icon: 'i-lucide-user',
        active: route.path === '/tasks/my'
      },
      {
        label: 'Team Tasks',
        to: '/tasks/team',
        icon: 'i-lucide-users',
        active: route.path === '/tasks/team'
      }
    ]
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
    label: 'Help',
    to: '/help',
    icon: 'i-lucide-help-circle',
    active: route.path === '/help',
    children:[
      {
        label: 'Documentation',
        to: '/help/documentation',
        icon: 'i-lucide-file-text',
        active: route.path === '/help/documentation'
      },
      {
        label: 'Call 24/7',
        to: '/help/call',
        icon: 'i-lucide-phone',
        active: route.path === '/help/call'
      }
    ]
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
    <UHeader title="Welcome" class=" text-center font-bold text-lg bg-gray-950 text-white">
      <UNavigationMenu
        :items="items"
        class="w-fullscreen "
      />
      <UInput type="file" />
    </UHeader>
    <UMain>
      <div class=" bg-gray-800 w-60 h-240">
        <UNavigationMenu
          orientation="vertical"
          :items="main"
          class="text-black text-center font-bold "
        />
      </div>
    </UMain>
    <UFooter class="bg-gray-950">
      <UNavigationMenu :items="menus" />
    </UFooter>
  </UApp>
</template>
