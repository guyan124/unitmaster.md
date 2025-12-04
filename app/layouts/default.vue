<!-- <script setup lang="ts">
const { data: navigation } = await useAsyncData('nav', ()=> {
    return queryCollectionNavigation('content')
})

</script>

<template>
 <UPage>

    <template #default>
        <slot/>
    </template>

    <template #left>
        <UPageAside>
            <UContentNavigation :navigation="navigation"/>
        </UPageAside>
    </template>
 </UPage>   
</template> -->


<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const { data: navigation } = await useAsyncData('nav', ()=> {
    return queryCollectionNavigation('content')
})


const items: NavigationMenuItem[][] = [[{
  label: 'Introduction',
  icon: 'i-lucide-house',
  active: true
}, {
  label: 'Inbox',
  icon: 'i-lucide-inbox',
  badge: '4'
}, {
  label: 'Contacts',
  icon: 'i-lucide-users'
}, {
  label: 'Settings',
  icon: 'i-lucide-settings',
  defaultOpen: true,
  children: [{
    label: 'General'
  }, {
    label: 'Members'
  }, {
    label: 'Notifications'
  }]
}], [{
  label: 'Feedback',
  icon: 'i-lucide-message-circle',
  to: 'https://github.com/nuxt-ui-templates/dashboard',
  target: '_blank'
}, {
  label: 'Help & Support',
  icon: 'i-lucide-info',
  to: 'https://github.com/nuxt/ui',
  target: '_blank'
}]]
</script>




 <template>
  <UDashboardGroup>
    <UDashboardSidebar
      collapsible
      resizable
      :ui="{ footer: 'border-t border-default' }">

      <template #header="{ collapsed }">
        <div class="flex items-center gap-2 px-3 py-2">
          <UIcon
            name="i-simple-icons-nuxtdotjs"
            class="size-5 text-primary"
          />
          <span v-if="!collapsed" class="font-semibold text-sm">
            Unit Master
          </span>
        </div>
      </template>

      <template #default="{ collapsed }">
        <UButton
          :label="collapsed ? undefined : 'Search...'"
          icon="i-lucide-search"
          color="neutral"
          variant="outline"
          block
          :square="collapsed"
        >
          <template v-if="!collapsed" #trailing>
            <div class="flex items-center gap-0.5 ms-auto">
              <UKbd value="meta" variant="subtle" />
              <UKbd value="K" variant="subtle" />
            </div>
          </template>
        </UButton>

        <!-- <UNavigationMenu
          :collapsed="collapsed"
          :items="items[0]"
          orientation="vertical"
        /> -->

        <UContentNavigation :collapsible="true" :navigation="navigation"/>

        <UNavigationMenu
          :collapsed="collapsed"
          :items="items[1]"
          orientation="vertical"
          class="mt-auto"
        />
      </template>

    

      <template #footer="{ collapsed }">
        <UButton
          
          :label="collapsed ? undefined : 'Support Ticket System'"
          color="neutral"
          variant="ghost"
          class="w-full"
          :block="collapsed"
        />
      </template>
    </UDashboardSidebar>

   <main class="p-20"><slot /></main>
  </UDashboardGroup>
</template>
