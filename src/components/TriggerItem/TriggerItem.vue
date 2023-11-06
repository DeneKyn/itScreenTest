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
    <div class="switch-element__black-square-border">
      <div class="switch-element__black-square">
        <div class="switch-element__light-square">
          <div class="switch-element__button-border" @click="() => onSwitchToggle()">
            <div class="switch-element__button"
              :class="isActive ? 'switch-element__button_color-green' : 'switch-element__button_color-red'">
              <span class="switch-element__text">{{ isActive ? 'СТАРТ' : 'СТОП' }}</span>
            </div>
          </div>
        </div>
        <div class="switch-element__button-shadow"></div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import url('./TriggerItem.scss');
</style>
