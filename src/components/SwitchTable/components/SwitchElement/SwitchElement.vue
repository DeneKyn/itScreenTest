<script setup lang="ts">
import { defineProps } from 'vue'
import './SwitchElement.scss'

defineProps(['id', 'isActive'])
</script>

<template>
  <div
    class="b-switch-element"
    :class="{ 'b-switch-element_active': isActive, 'b-switch-element_unactive': !isActive }"
  >
    <div class="b-switch-element__body">
      <div class="b-body__indicator">
        <div
          class="b-indicator__ligther"
          :class="{ 'b-indicator__ligther_active': isActive }"
        ></div>
        <div class="b-indicator__label">ВКЛ</div>
      </div>
      <div class="b-body__indicator">
        <div class="b-indicator__label">ВЫКЛ</div>
        <div
          class="b-indicator__ligther"
          :class="{ 'b-indicator__ligther_unactive': !isActive }"
        ></div>
      </div>
    </div>
  </div>
</template>
