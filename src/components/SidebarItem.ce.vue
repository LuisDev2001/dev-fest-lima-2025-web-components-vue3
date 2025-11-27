<script setup lang="ts">
import { Icon } from '@iconify/vue'

export interface Props {
  icon: string
  label: string
  isActive?: boolean
}

const props = defineProps<Props>()

const emits = defineEmits(['click'])
</script>

<template>
  <li
    class="flex items-center justify-start gap-2 p-2.5 rounded-lg cursor-pointer transition-all"
    :class="[props.isActive ? 'text-sky-600 bg-blue-200' : 'text-slate-600 hover:bg-gray-100']"
    @click="emits('click')"
  >
    <Icon :icon="props.icon" width="20" height="20" />
    <span class="text-sm" :class="[props.isActive ? 'text-sky-600 font-bold' : 'font-medium ']">
      {{ props.label }}
    </span>
  </li>
</template>
