<script setup lang="ts">
import { defineProps } from 'vue'
import './TriggerElement.scss'

const props = defineProps(['id', 'isActive'])
</script>

<template>
  <div class="b-trigger" v-bind:class="{ 'b-trigger_active': isActive }">
    <div class="b-trigger__title">
      {{ isActive ? 'Старт' : 'стоп' }}
    </div>
  </div>
</template>
