<script setup lang="ts">
import { defineProps, ref } from 'vue'
import './SwitchItem.scss'

defineProps(['id'])
defineEmits(['copy'])
const isActive = ref(false)

const handleOnClick = () => {
  isActive.value = !isActive.value
}
</script>

<template>
  <div class="b-switch-item">
    <slot name="header" />
    <div class="b-switch-item__body">
      <input type="checkbox" :id="'light-switch_' + id" class="b-body__input" />
      <label :for="'light-switch_' + id" class="b-body__label">
        <div class="b-label__body" @click="handleOnClick">
          <slot name="body" v-bind:isActive="isActive" />
        </div>
      </label>
    </div>
  </div>
</template>
