<script setup lang="ts">
import IconLogo from './icons/IconLogo.vue';
import IconClose from './icons/IconClose.vue';

defineProps<{
    title: string,
}>()
</script>

<template>
    <div class="header">
        <div class="title">
            <div class="icon">
                <IconLogo></IconLogo>
            </div>
            <span>{{ title }}</span>
        </div>
        <div class="icon">
            <IconClose></IconClose>
        </div>
    </div>
</template>

<style scoped lang="scss">
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .icon {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .title {
        display: flex;
        gap: 8px;
        text-transform: uppercase;
        color: #FFF;
        font-family: Inter;
        font-size: 40px;
        font-style: normal;
        font-weight: 600;
        height: 48px;
    }
}
</style>