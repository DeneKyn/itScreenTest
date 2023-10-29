<script setup lang="ts">
import { ref } from 'vue'
import SwitchItem from '../components/SwitchItem/SwitchItem.vue'
import GearIcon from '../components/icons/GearIcon.vue'
import BucketIcon from '../components/icons/BucketIcon.vue'
import CopyIcon from '../components/icons/CopyIcon.vue'
import BurgerMenu from '../share/BurgerMenu.vue'

const initItems = new Array(8).fill('').map((el, ind) => ({
  title: `Title ${ind}`
}))

const menuItems: Array<{ icon: any; title: string; type: string }> = [
  { icon: GearIcon, title: 'Настроить', type: 'setup' },
  { icon: CopyIcon, title: 'Дублировать', type: 'copy' },
  { icon: BucketIcon, title: 'Удалить', type: 'delete' }
]

const items = ref(initItems)

const onMenuAction = (type: string, el: { title: string }) => {
  console.log(type)
  switch (type) {
    case 'copy':
      items.value = [...items.value, el]
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
  <main>
    <ul class="switch-wrapper">
      <li v-for="(el, index) in items" :key="index">
        <SwitchItem :id="index.toString()">
          <div class="header">
            <h2>{{ el.title }}</h2>
            <BurgerMenu @menu-action="(e) => onMenuAction(e, el)" :items="menuItems" /></div
        ></SwitchItem>
      </li>
    </ul>
  </main>
</template>

<style scoped lang="scss">
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;

  display: flex;
  justify-content: center;
  align-items: flex-start;
  align-content: flex-start;
  gap: 30px;
  flex-wrap: wrap;

  li {
    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;

      h2 {
        color: #fff;
        font-family: Inter;
        font-size: 18px;
        font-style: normal;
        font-weight: 700;
        line-height: normal;
      }
    }

    border-radius: 4px;
    border: 2px solid rgba(255, 255, 255, 0.2);
    padding: 20px;
  }
}
</style>
