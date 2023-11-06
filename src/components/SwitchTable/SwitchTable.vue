<script lang="ts">
import { defineComponent, shallowRef } from 'vue'
import SwitchItem from '../SwitchItem/SwitchItem.vue'
import TriggerItem from '../TriggerItem/TriggerItem.vue'
import IconGear from '../icons/IconGear.vue'
import IconBucket from '../icons/IconBucket.vue'
import IconCopy from '../icons/IconCopy.vue'
import ContextMenu from '../../share/ContextMenu.vue'

export default defineComponent({
  components: {
    SwitchItem,
    TriggerItem,
    IconGear,
    IconBucket,
    IconCopy,
    ContextMenu
  },
  setup() {
    const initItems = new Array(8).fill('').map((el, index) => ({
      title: `Table Light ${index}`,
      component: index >= 2 ? SwitchItem : TriggerItem,
      isActive: false
    }));
    const initMenuItems = [
      { icon: IconGear, title: 'Настроить', type: 'setup' },
      { icon: IconCopy, title: 'Дублировать', type: 'copy' },
      { icon: IconBucket, title: 'Удалить', type: 'delete' }
    ]
    return {
      items: shallowRef(initItems),
      menuItems: shallowRef(initMenuItems),
    };
  },
  methods: {
    onMenuAction(type: string, id: number) {
      switch (type) {
        case 'copy':
          this.items = [...this.items, ...[this.items[id]]];
          break
        case 'delete':
          this.items.splice(id, 1);
          this.items = [...this.items];
          break
        default:
          break
      }
    },
    onToggleSwitch(id: string) {
      this.items[+id] = {
        title: this.items[+id].title,
        component: this.items[+id].component,
        isActive: !this.items[+id].isActive
      }
      this.items = [...this.items]
    }
  }
})
</script>

<template>
  <section class="table">
    <div class="table__wrapper">
      <ul class="table__items">
        <li class="table-item" v-for="(el, index) in items" :key="index">
          <component :is="el.component" :id="index.toString()" :isActive="el.isActive"
            @toggle="(e: string) => onToggleSwitch(e)">
            <div class="table-item__header">
              <h2 class="table-item__title">{{ el.title }}</h2>
              <ContextMenu @menu-action="(e) => onMenuAction(e, index)" :items="menuItems" />
            </div>
          </component>
        </li>
      </ul>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import url('./SwitchTable.scss');
</style>
