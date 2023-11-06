<script lang="ts">
import { defineComponent, ref } from 'vue'
import IconMenu from '../components/icons/IconMenu.vue'

interface IItems {
  icon: any,
  title: string,
  type: string,
}

export default defineComponent({
  components: {
    IconMenu,
  },
  setup() {
    const menuList = ref(null);
    return {
      menuList,
    };
  },
  emits: ['menu-action'],
  props: {
    items: Array<IItems>,
  },
  data() {
    return {
      isActive: false,
      isMounted: false,
      top: '0px',
      left: '0px',
    }
  },
  mounted() {
    this.isMounted = true;
    document.querySelector(".main-page__content")?.addEventListener('scroll', () => {
      this.closeMenu();
    });
  },
  methods: {
    toggleMenu() {
      this.isActive = !this.isActive;
    },
    closeMenu() {
      this.isActive = false;
    },
    onMenuItemClick(type: string) {
      this.$emit('menu-action', type);
      this.toggleMenu();
    },
    onClick(event: Event) {
      const el = event.currentTarget as HTMLElement;
      const targetRect = el.getBoundingClientRect();
      this.top = `${targetRect.top + targetRect.height + 5}px`;
      this.left = `${targetRect.left + targetRect.width}px`;
      if (document.body.clientWidth <= targetRect.left + targetRect.width + 160) {
        this.left = `${document.body.clientWidth - 160 - 5}px`;
      }
      this.toggleMenu();
    },
  }
})

</script>

<template>
  <div class="context-menu-icon" @click="onClick">
    <IconMenu></IconMenu>
  </div>
  <Teleport to="#app" v-if="isMounted && isActive">
    <section class="context-menu" v-bind:style="{ 'top': top, 'left': left }">
      <div class="context-menu__wrapper">
        <div class="context-menu__items" @mouseleave="closeMenu" v-if="isActive">
          <div class="context-menu-item" v-for="(item, index) in items" :key="index"
            @click="() => onMenuItemClick(item.type)">
            <component class="context-menu-item__icon" :is="item.icon"></component>
            <div class="context-menu-item__title">{{ item?.title }}</div>
          </div>
        </div>
      </div>
    </section>
  </Teleport>
</template>


<style lang="scss" scoped>
@import url('./ContextMenu.scss');
</style>