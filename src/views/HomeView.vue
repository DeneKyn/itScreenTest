<script setup lang="ts">
import SwitchTable from '@/components/SwitchTable/SwitchTable.vue'
import HeaderComponent from '@/components/Header/HeaderComponent.vue'
import backgroundImg from '../assets/background.svg'
import './HomeView.scss'
</script>
<template>
  <main class="b-view b-view-home">
    <HeaderComponent title="GARDEN LIGHT" />
    <SwitchTable />
    <div class="b-view-home__background-image">
      <img :src="backgroundImg" alt="background" />
    </div>
  </main>
</template>
