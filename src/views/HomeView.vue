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
  <div class="ellipseBottom"></div>
  <div class="ellipseTop"></div>
  <div class="faq" @click="handleFAQ()">
    <IconFAQ></IconFAQ>
  </div>
  <div class="layout">
    <header>
      <HeaderComponent :title="title"> </HeaderComponent>
    </header>
    <main>
      <SwitchTable></SwitchTable>
    </main>
    <footer>
      <FooterComponent></FooterComponent>
    </footer>
  </div>
</template>

<style scoped lang="scss">
.ellipseBottom {
  position: absolute;
  height: 50%;
  width: 40%;
  bottom: 0;
  left: 0;

  background-repeat: no-repeat;
  background-size: cover;
  background-image: url('@/assets/ellipseBottom.png');
}

.ellipseTop {
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

.layout {
  display: flex;
  flex: auto;
  flex-direction: column;
  height: 100%;
  margin: 0 50px;
  max-height: 100vh;
  max-width: 1620px;

  header {
    line-height: 48px;
    margin-top: 50px;
    margin-bottom: 50px;
    z-index: 1;
  }

  main {
    display: flex;
    flex-direction: column;
    flex: 1;
    min-height: 120px;
    overflow: auto;
    z-index: 1;
  }

  footer {
    text-align: center;
    color: #fff;
    margin-top: 5px;
    margin-bottom: 20px;
    z-index: 1;
  }
}
</style>
