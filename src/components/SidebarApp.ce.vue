<script setup lang="ts">
import { ref } from 'vue'
import { Icon } from '@iconify/vue'
import SidebarItem from './SidebarItem.ce.vue'

export interface Props {
  copy?: string
}

const props = defineProps<Props>()

const items = [
  {
    icon: 'mdi:home-outline',
    label: 'Dashboard',
  },
  {
    icon: 'mdi:folder-outline',
    label: 'Projects',
  },
  {
    icon: 'mdi:account-group-outline',
    label: 'Team',
  },
  {
    icon: 'mdi:home-analytics',
    label: 'Analytics',
  },
  {
    icon: 'mdi:credit-card-outline',
    label: 'Billing',
  },
]

const activeItemIndex = ref(0)

const handleToggleIsActive = (index: number) => {
  activeItemIndex.value = index
}
</script>

<template>
  <aside class="w-64 h-dvh bg-white p-4 border-r border-gray-200 border-solid flex flex-col">
    <div class="flex items-center justify-start gap-2 mb-6">
      <div class="bg-blue-600 w-10 h-10 flex items-center justify-center text-white rounded-lg">
        <Icon icon="mdi:view-dashboard" width="24" height="24" color="white"></Icon>
      </div>
      <span class="font-bold text-xl"> My Saas </span>
    </div>

    <ul class="space-y-2 flex-1">
      <SidebarItem
        v-for="(item, index) in items"
        :key="item.label"
        :icon="item.icon"
        :label="item.label"
        :is-active="activeItemIndex === index"
        @click="handleToggleIsActive(index)"
      />
    </ul>

    <div>
      <hr class="h-px bg-gray-200 border-0 my-2" />
      <ul class="space-y-2">
        <SidebarItem icon="mdi:cog-outline" label="Settings"></SidebarItem>

        <SidebarItem icon="mdi:account-circle-outline" label="User Profile"></SidebarItem>

        <div v-if="props.copy">
          <span class="text-sm text-gray-400">
            {{ props.copy }}
          </span>
        </div>
      </ul>
    </div>
  </aside>
</template>
