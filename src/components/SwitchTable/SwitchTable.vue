<script setup lang="ts">
import { shallowRef } from 'vue'
import './SwitchTable.scss';
import SwitchItem from '../SwitchItem/SwitchItem.vue'
import TriggerItem from '../TriggerItem/TriggerItem.vue'
import IconGear from '../icons/IconGear.vue'
import IconBucket from '../icons/IconBucket.vue'
import IconCopy from '../icons/IconCopy.vue'
import BurgerMenu from '../../share/BurgerMenu.vue'

const initItems = new Array(8).fill('').map((el, index) => ({
    title: `Table Light ${index}`,
    component: index >= 2 ? SwitchItem : TriggerItem,
    isActive: false,
}))

const menuItems: Array<{ icon: any; title: string; type: string }> = [
    { icon: IconGear, title: 'Настроить', type: 'setup' },
    { icon: IconCopy, title: 'Дублировать', type: 'copy' },
    { icon: IconBucket, title: 'Удалить', type: 'delete' }
]

const items = shallowRef(initItems)

const onMenuAction = (type: string, el: { title: string, component: typeof SwitchItem | typeof TriggerItem, isActive: boolean }) => {
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
const onToggleSwitch = (id: string) => {
    items.value[+id] = { title: items.value[+id].title, component: items.value[+id].component, isActive: !items.value[+id].isActive };
    items.value = [...items.value]
}

</script>

<template>
    <ul class="switch-wrapper">
        <li v-for="(el, index) in items" :key="index">
            <component :is="el.component" :id="index.toString()" :isActive="el.isActive"
                @toggle="(e: string) => onToggleSwitch(e)">
                <div class=" header">
                    <h2>{{ el.title }}</h2>
                    <BurgerMenu @menu-action="(e) => onMenuAction(e, el)" :items="menuItems" />
                </div>
            </component>
        </li>
    </ul>
</template>
