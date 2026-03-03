<script setup lang="ts">
import type { NavigateBar, NavigateFooter, NavigateMain } from '@nuxt/ui'
import { CalendarDate } from '@internationalized/date'

const inputeDate = useTemplateRef('inputDate')

const today = new Date()

const modelValue = shallowRef(new CalendarDate(
  today.getFullYear(),
  today.getMonth() + 1,
  today.getDate()
))

const route = useRoute()

const items = computed<NavigateBar[]>(() => [
  {
    label: 'Home',
    to: '/',
    icon: 'i-lucide-home',
    active: route.path === '/'
  },
  {
    label: 'Profile',
    to: '/profile',
    icon: 'i-lucide-user',
    active: route.path === '/profile'
  },
  {
    label: 'Dashboard',
    to: '/dashboard',
    icon: 'i-lucide-layout-dashboard',
    active: route.path === '/dashboard'
  },
  {
    label:'Tasks',
    to: '/tasks',
    icon: 'i-lucide-list-check',
    active: route.path === '/tasks'
  },
  {
    label: 'Settings',
    to: '/settings',
    icon: 'i-lucide-settings',
    active: route.path === '/settings'
  },
  {
    label: 'Contacts',
    to: '/contacts',
    icon: 'i-lucide-users',
    active: route.path === '/contacts'
  },
  {
    label: 'Support Center',
    to: '/support',
    icon: 'i-lucide-headphones',
    active: route.path === '/support'
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
  },
])


const state = reactive({ fullName: '' })

async function onSubmit() {
  return new Promise<void>(res => setTimeout(res, 1000))
}

async function validate(data: Partial<typeof state>) {
  if (!data.fullName?.length) return [{ name: 'fullName', message: 'Required' }]
  return []
}
</script>

<template>
  <UApp>
    <UHeader title="Welcome" class=" text-center font-bold text-lg bg-gray-950 text-white">
      <template #body>
        <div class="space-y-4">
          <UNavigationMenu :items="items" orientation="vertical" class="w-48" />
        </div>
      </template>
    </UHeader>
    <UMain class="p-5">
      <UUser name="Admin" description="FullStack Developer" :avatar="{
      }" :chip="{
        color: 'primary',
        position: 'top-right',
      }" />
      <UForm :state="state" :validate="validate" @submit="onSubmit">
        <UFormField class="mt-5" name="fullName" label="Subject">
          <UInput v-model="state.fullName" />
          <UButton type="submit" class="mt-2 ml-2" loading-auto>
            Submit
          </UButton>
        </UFormField>
      </UForm>
      <UInputDate ref="inputDate" v-model="modelValue" class="mt-5">
        <template #trailing>
          <UPopover :reference="inputeDate?.inputsRef[3]?.$el">
            <UButton color="neutral" variant="link" size="sm" aria-label="Select Date" class="px-0"
              icon="i-lucide-calendar" />
            <template #content>
              <UCalendar v-model="modelValue" />
            </template>
          </UPopover>
        </template>
      </UInputDate>
      <UPricingPlan class="p-5 border rounded-lg shadow-md bg-black max-w-sm mx-auto mt-10" title="Promotion"
        description="For bootstrappers" price="$249.99" :features="[
          'One Developer',
          'Unlimited Plan',
          'Access to Github',
          'Unlimited Patch & minor updates',
          'Lifetime Access'
        ]" :button="{
          label: 'Buy Now'
        }" highlight />
    </UMain>
    <UFooter class="bg-gray-950">
      <UNavigationMenu :items="menus" />
    </UFooter>
    <RouterView />
  </UApp>
</template>
