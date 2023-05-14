<script>
import { BUTTON_TYPE_DANGER, BUTTON_TYPE_NEUTRAL, BUTTON_TYPE_PRIMARY } from '../constants'
import { isButtonTypeValid } from '../validators'

const typeClasses = {
  [BUTTON_TYPE_PRIMARY]: 'enabled:hover:bg-purple-600 bg-purple-500 text-white',
  [BUTTON_TYPE_NEUTRAL]: 'enabled:hover:bg-gray-200 bg-gray-100',
  [BUTTON_TYPE_DANGER]: 'enabled:hover:bg-red-600 bg-red-500 text-white'
}
</script>

<script setup>
defineProps({
  type: {
    default: BUTTON_TYPE_PRIMARY,
    type: String,
    validator: isButtonTypeValid
  }
})
</script>

<template>
  <button
    :class="`${typeClasses[type]} rounded p-3 disabled:cursor-not-allowed disabled:opacity-50`"
  >
    <slot></slot>
  </button>
</template>
