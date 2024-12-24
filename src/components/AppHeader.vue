<script setup lang="ts">
import { ComputedRef, ref } from 'vue'

interface IMenuItem {
  label: string
  icon: string
  path: string
  show: ComputedRef<boolean>
}

const items = ref<IMenuItem[]>([
  {
    label: 'Authorizatiion',
    icon: 'pi pi-user',
    path: '/auth',
    // show: computed((): boolean => !userStore.userId)
  },
  {
    label: 'Add',
    icon: 'pi pi-plus',
    path: '/',
    // show: computed((): boolean => !!userStore.userId)
  },
  {
    label: 'Interviews List',
    icon: 'pi pi-list',
    path: '/list',
    // show: computed((): boolean => !!userStore.userId)
  },
  {
    label: 'Statistic',
    icon: 'pi pi-chart-pie',
    path: '/statistic',
    // show: computed((): boolean => !!userStore.userId)
  },
])
</script>

<template>
  <app-menubar :model="items" class="menu">
    <template #item="{ item, props }">
      <router-link :to="item.path" class="flex align-items-center" v-bind="props.action">
        <span :class="item.icon" class="p-menuitem-icon"></span>
        <span class="ml-2">{{ item.label }}</span>
      </router-link>
    </template>
  </app-menubar>
</template>

<style scoped>
.menu {
  margin: 30px 0;
}

.menu-exit {
  cursor: pointer;
}
</style>
