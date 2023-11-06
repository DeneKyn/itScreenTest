<script setup lang="ts">
import { defineProps } from 'vue'
import IconLogo from '../icons/IconLogo.vue'
import IconClose from '../icons/IconClose.vue'
import './HeaderComponent.scss'

defineProps(['title'])

const handleClose = () => {
  alert('TODO: Add Action')
}
</script>

<template>
  <div class="b-header">
    <div class="b-header__title">
      <div class="title__icon">
        <IconLogo></IconLogo>
      </div>
      <span>{{ title }}</span>
    </div>
    <div class="b-header__close-icon" @click="handleClose()">
      <IconClose></IconClose>
    </div>
  </div>
</template>
