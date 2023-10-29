<script setup lang="ts">
import { defineProps } from 'vue';
import IconLogo from '../icons/IconLogo.vue';
import IconClose from '../icons/IconClose.vue';
import './HeaderComponent.scss'

defineProps(['title']);

const handleClose = () => {
    alert("TODO: Add Action");
}

</script>

<template>
    <div class="header">
        <div class="title">
            <div class="icon">
                <IconLogo></IconLogo>
            </div>
            <span>{{ title }}</span>
        </div>
        <div class="icon" @click="handleClose()">
            <IconClose></IconClose>
        </div>
    </div>
</template>
