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
  <div @click="onClick" class="b-burger-menu">
    <IconMenu></IconMenu>
    <div @mouseleave="closeMenu" v-if="isActive" class="b-burger-menu__list">
      <div @click="() => onMenuItemClick(item.type)" class="list__item" v-for="item in items">
        <component :is="item.icon"></component>
        <div class="item__title">{{ item?.title }}</div>
      </div>
    </div>
  </div>
</template>
