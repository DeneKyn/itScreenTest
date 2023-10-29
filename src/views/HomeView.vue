<script setup lang="ts">
import SwitchTable from '../components/SwitchTable.vue'
import HeaderComponent from '../components/HeaderComponent.vue'
import FooterComponent from '../components/FooterComponent.vue'
import IconFAQ from '../components/icons/IconFAQ.vue'

</script>
<template>
  <div class="ellipseBottom"></div>
  <div class="ellipseTop"></div>
  <div class="faq">
    <IconFAQ></IconFAQ>
  </div>
  <div class="layout">
    <header>
      <HeaderComponent :title="'Garden Light'"> </HeaderComponent>
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
  ;
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
  ;
}

.faq {
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
  }

  main {
    display: flex;
    flex-direction: column;
    flex: 1;
    min-height: 120px;
    line-height: 120px;
    overflow: auto;
  }

  footer {
    text-align: center;
    color: #fff;
    margin-top: 5px;
    margin-bottom: 20px;
  }
}
</style>
