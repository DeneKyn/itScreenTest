<script lang="ts">
import { defineComponent } from 'vue'
import IconLogo from '../icons/IconLogo.vue'
import IconClose from '../icons/IconClose.vue'

export default defineComponent({
  components: {
    IconLogo,
    IconClose,
  },
  props: {
    title: { type: String, required: true }
  },
  methods: {
    handleClose() {
      alert('TODO: Add Action')
    }
  }
})

</script>

<template>
  <section class="header">
    <div class="header__wrapper">
      <div class="header__logo">
        <div class="header__icon">
          <IconLogo></IconLogo>
        </div>
        <span class="header__title">{{ title }}</span>
      </div>
      <div class="header__icon" @click="handleClose()">
        <IconClose></IconClose>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import url('./HeaderComponent.scss');
</style>