<script setup lang="ts">
import { defineProps } from 'vue'

defineProps(['id', 'isActive'])
const emit = defineEmits(['toggle'])

const onSwitchToggle = (id: string) => {
  emit('toggle', id)
}
</script>

<template>
  <slot />
  <div class="switch-element">
    <div :for="'light-switch_' + id" class="cnt1-border-wrap">
      <div class="cnt1">
        <div class="cnt2">
          <div class="cnt3-border-wrap" @click="() => onSwitchToggle(id)">
            <div class="cnt3" :class="isActive ? 'on' : 'off'">
              {{ isActive ? 'Стоп' : 'Старт' }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import url('./TriggerItem.scss');
</style>
