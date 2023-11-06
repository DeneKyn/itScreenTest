<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  emits: ['toggle',],
  props: {
    id: { type: String, required: true },
    isActive: { type: Boolean, required: true }
  },
  methods: {
    handleClose() {
      alert('TODO: Add Action')
    }
  }
})
</script>

<template>
  <slot />
  <div class="switch-element">
    <input type="checkbox" :id="'light-switch_' + id" />
    <label :for="'light-switch_' + id" class="cnt1-border-wrap">
      <div class="cnt1">
        <div class="cnt2">
          <div class="cnt3-border-wrap">
            <div class="cnt3">
              <div class="switch-indicator-block indicator-on">
                <div class="switch-indicator-wrap">
                  <div class="switch-indicator"></div>
                </div>
                <span class="switch-indicator-label"> ВКЛ </span>
              </div>

              <div class="switch-indicator-block indicator-off">
                <span class="switch-indicator-label"> ВЫКЛ </span>
                <div class="switch-indicator-wrap">
                  <div class="switch-indicator"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="cnt2-shadow"></div>
      </div>
    </label>
  </div>
</template>

<style lang="scss" scoped>
@import url('./SwitchItem.scss');
</style>
