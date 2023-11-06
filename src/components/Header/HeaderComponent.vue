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
  <div class="header">
    <div class="title">
      <div class="icon">
        <IconLogo></IconLogo>
      </div>
      <span>{{ title }}</span>
    </div>
    <div class="icon" @click="handleClose()">
      <IconClose></IconClose>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import url('./HeaderComponent.scss');
</style>