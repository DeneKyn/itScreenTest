<script setup lang="ts">
import { ref } from 'vue'
import './SwitchTable.scss';
import SwitchItem from '../SwitchItem/SwitchItem.vue'
import IconGear from '../icons/IconGear.vue'
import IconBucket from '../icons/IconBucket.vue'
import IconCopy from '../icons/IconCopy.vue'
import BurgerMenu from '../../share/BurgerMenu.vue'

const initItems = new Array(8).fill('').map((el, ind) => ({
    title: `Title ${ind}`
}))

const menuItems: Array<{ icon: any; title: string; type: string }> = [
    { icon: IconGear, title: 'Настроить', type: 'setup' },
    { icon: IconCopy, title: 'Дублировать', type: 'copy' },
    { icon: IconBucket, title: 'Удалить', type: 'delete' }
]

const items = ref(initItems)

const onMenuAction = (type: string, el: { title: string }) => {
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
    <ul class="switch-wrapper">
        <li v-for="(el, index) in items" :key="index">
            <SwitchItem :id="index.toString()">
                <div class="header">
                    <h2>{{ el.title }}</h2>
                    <BurgerMenu @menu-action="(e) => onMenuAction(e, el)" :items="menuItems" />
                </div>
            </SwitchItem>
        </li>
    </ul>
</template>
