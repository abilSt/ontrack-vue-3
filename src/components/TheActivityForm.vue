<script setup>
import { nextTick, ref } from 'vue'
import BaseButton from '../components/BaseButton.vue'
import { PlusIcon } from '@heroicons/vue/24/outline'
import { isActivityValid } from '../validators'
import { id } from '../functions'

const emit = defineEmits({
  submit: isActivityValid
})

const name = ref('')

async function submit() {
  emit('submit', {
    id: id(),
    name: name.value,
    secondsToComplete: 0
  })
  name.value = ''

  await nextTick()
  window.scrollTo(0, document.body.scrollHeight)
}
</script>

<template>
  <form
    @submit.prevent="submit"
    class="sticky bottom-[57px] flex gap-2 border-t bg-white p-4"
  >
    <input
      v-model="name"
      type="text"
      class="w-full rounded border px-4 text-xl"
      placeholder="Activity name"
    />
    <BaseButton :disabled="name.trim() === ''">
      <PlusIcon class="h-8" />
    </BaseButton>
  </form>
</template>
