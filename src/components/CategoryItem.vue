<template>
  <button @click="onButtonClicked" class="pill-button m-1" :class="{ 'active': isActive }">
    {{ props.title }}</button>
</template>

<script setup lang="ts">
const props = defineProps({
  title: String,
  isActive: Boolean,
})
const emit = defineEmits(['onButtonClicked'])

const onButtonClicked = () => {
  emit('onButtonClicked')
}
</script>
