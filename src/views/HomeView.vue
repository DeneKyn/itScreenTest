<script lang="ts">
import { defineComponent } from 'vue'
import SwitchTable from '../components/SwitchTable/SwitchTable.vue'
import HeaderComponent from '../components/Header/HeaderComponent.vue'
import FooterComponent from '../components/Footer/FooterComponent.vue'
import IconFAQ from '../components/icons/IconFAQ.vue'

export default defineComponent({
  components: {
    SwitchTable,
    HeaderComponent,
    FooterComponent,
    IconFAQ
  },
  data() {
    return {
      title: 'Garden Light'
    }
  },
  mounted() {},
  methods: {
    handleFAQ() {
      alert('TODO: Add Action')
    }
  }
})
</script>

<template>
  <div class="faq" @click="handleFAQ()">
    <IconFAQ></IconFAQ>
  </div>
  <div class="main-page">
    <header class="main-page__header">
      <HeaderComponent :title="title"> </HeaderComponent>
    </header>
    <main class="main-page__content">
      <SwitchTable></SwitchTable>
    </main>
    <footer class="main-page__footer">
      <FooterComponent></FooterComponent>
    </footer>
  </div>
</template>

<style lang="scss">
.bg-ellipse-bottom {
  position: absolute;
  height: 50%;
  width: 40%;
  bottom: 0;
  left: 0;

  background-repeat: no-repeat;
  background-size: cover;
  background-image: url('@/assets/ellipseBottom.png');
}

.bg-ellipse-top {
  position: absolute;
  width: 350px;
  height: 55%;
  top: 0;
  right: 0;

  background-repeat: no-repeat;
  background-size: cover;
  background-image: url('@/assets/ellipseTop.png');
}

.faq {
  cursor: pointer;
  position: absolute;
  bottom: 10px;
  right: 10px;
  height: 40px;
  width: 40px;
}

.main-page {
  display: flex;
  flex: auto;
  flex-direction: column;
  height: 100%;
  padding: 0 50px;
  margin: auto;
  max-height: 100vh;
  max-width: 1620px;

  &__header {
    z-index: 1;
  }

  &__content {
    position: relative;
    display: flex;
    flex-direction: column;
    flex: 1;
    min-height: 120px;
    overflow: auto;
    z-index: 1;
  }

  &__footer {
    z-index: 1;
  }
}
</style>
