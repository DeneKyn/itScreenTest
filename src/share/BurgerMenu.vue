<script setup lang="ts">
import { ref, type PropType } from 'vue'
import IconMenu from '../components/icons/IconMenu.vue'
import './BurgerMenu.scss'
defineProps(['items'])
const emit = defineEmits(['menu-action'])
const isActive = ref(false)
const onClick = () => {
  isActive.value = !isActive.value
}
const closeMenu = () => {
  isActive.value = false
}
const onMenuItemClick = (type: string) => {
  emit('menu-action', type)
  onClick()
}
</script>

<template>
  <div class="container">
    <IconMenu @click="onClick"></IconMenu>
    <div @mouseleave="closeMenu" v-if="isActive" class="menu_list">
      <div v-for="(item, index) in items" :key="index" @click="() => onMenuItemClick(item.type)" class="menu_item">
        <component :is="item.icon"></component>
        <div>{{ item?.title }}</div>
      </div>
    </div>
  </div>
</template>
