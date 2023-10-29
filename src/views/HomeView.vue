<script setup lang="ts">
import SwitchItem from '../components/SwitchItem.vue'
import IconMenu from '../components/icons/IconMenu.vue'

const items: Array<any> = [{ title: 'Table Light 01' }, { title: 'Table Light 02' }, { title: 'Table Light 03' }, { title: 'Table Light 04' }, { title: 'Table Light 05' }, { title: 'Table Light 06' }]
</script>

<template>
  <main>

    <ul class="switch-wrapper">

      <li v-for="({ title }, index) in items" :key="index">
        <div class="header">
          <h2>{{ title }}</h2>
          <IconMenu></IconMenu>
        </div>
        <SwitchItem :id="index.toString()"></SwitchItem>
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
        color: #FFF;
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
