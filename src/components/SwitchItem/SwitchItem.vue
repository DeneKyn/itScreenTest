<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  emits: ['toggle',],
  props: {
    id: { type: String, required: true },
    isActive: { type: Boolean, required: true }
  },
  data() {
    return {
      isChecked: this.isActive,
    }
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
    <label class="switch-element__label">
      <input class="switch-element__input" type="checkbox" v-model="isChecked" />
      <div class="switch-element__black-square">
        <div class="switch-element__light-square" :class="[isChecked ?
          'switch-element__light-square_color-on' :
          'switch-element__light-square_color-off']">
          <div class="switch-element__button-border" :class="[isChecked ?
            'switch-element_button-border__position-top' :
            'switch-element__button-border_position-bottom']">
            <div class="switch-element__button">

              <div class="switch-indicator switch-indicator_position-top">
                <div class="switch-indicator__wrapper">
                  <div class="switch-indicator__light switch-indicator__light_color-off"
                    :class="{ 'switch-indicator__light_color-green': isChecked }"></div>
                  <span class="switch-indicator__label"> ВКЛ </span>
                </div>
              </div>

              <div class="switch-indicator switch-indicator_position-bottom">
                <div class="switch-indicator__wrapper">
                  <div class="switch-indicator__light switch-indicator__light_color-off"
                    :class="{ 'switch-indicator__light_color-red': !isChecked }"></div>
                  <span class="switch-indicator__label"> ВЫКЛ </span>
                </div>
              </div>

            </div>
          </div>
        </div>
        <div class="switch-element__button-shadow"></div>
      </div>
    </label>
  </div>
</template>

<style lang="scss" scoped>
@import url('./SwitchItem.scss');
</style>
