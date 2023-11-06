<script setup lang="ts">
import { shallowRef } from 'vue'
import './SwitchTable.scss'
import SwitchItem from './SwitchItem/SwitchItem.vue'
import SwitchElement from './components/SwitchElement/SwitchElement.vue'
import TriggerElement from './components/TriggerElement/TriggerElement.vue'
import IconGear from '../icons/IconGear.vue'
import IconBucket from '../icons/IconBucket.vue'
import IconCopy from '../icons/IconCopy.vue'
import BurgerMenu from '../../share/BurgerMenu.vue'

const getType = (types: Array<string>) => {
  const index = Math.floor(Math.random() * types.length)
  return types[index]
}

const initItems = new Array(8).fill('').map((el, index) => ({
  title: `Table Light ${index}`,
  component: SwitchItem,
  isActive: false,
  type: getType(['switch', 'trigger'])
}))

const menuItems: Array<{ icon: any; title: string; type: string }> = [
  { icon: IconGear, title: 'Настроить', type: 'setup' },
  { icon: IconCopy, title: 'Дублировать', type: 'copy' },
  { icon: IconBucket, title: 'Удалить', type: 'delete' }
]

const items = shallowRef(initItems)

const onMenuAction = (
  type: string,
  el: { title: string; component: typeof SwitchItem; isActive: boolean; type: string }
) => {
  switch (type) {
    case 'copy':
      items.value = [...items.value, ...[el]]
      break
    case 'delete':
      items.value = items.value.filter(({ title }) => title !== el.title)
      break
    default:
      break
  }
}
</script>

<template>
  <ul class="b-switch-table">
    <li v-for="(el, index) in items" :key="index">
      <component :is="el.component" :id="index.toString()" :isActive="el.isActive">
        <template v-slot:header>
          <div class="b-switch-table__header">
            <h2>{{ el.title }}</h2>
            <BurgerMenu @menu-action="(e) => onMenuAction(e, el)" :items="menuItems" />
          </div>
        </template>
        <template v-slot:body="{ isActive }">
          <template v-if="el.type === 'trigger'"><TriggerElement :isActive="isActive" /></template>
          <template v-if="el.type === 'switch'"><SwitchElement :isActive="isActive" /></template>
        </template>
      </component>
    </li>
  </ul>
</template>
