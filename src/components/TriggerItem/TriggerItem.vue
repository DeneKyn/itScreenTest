<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  emits: ['toggle'],
  props: {
    id: { type: String, required: true },
    isActive: { type: Boolean, required: true }
  },
  methods: {
    onSwitchToggle() {
      this.$emit('toggle', this.id)
    }
  }
})
</script>

<template>
  <slot />
  <div class="switch-element">
    <div :for="'light-switch_' + id" class="cnt1-border-wrap">
      <div class="cnt1">
        <div class="cnt2">
          <div class="cnt3-border-wrap" @click="() => onSwitchToggle()">
            <div class="cnt3" :class="isActive ? 'on' : 'off'">
              {{ isActive ? 'СТАРТ' : 'СТОП' }}
            </div>
          </div>
        </div>
        <div class="cnt2-shadow"></div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import url('./TriggerItem.scss');
</style>
