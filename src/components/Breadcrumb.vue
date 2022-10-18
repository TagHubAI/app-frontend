<template>
  <n-breadcrumb class="inline-block">
    <div class="justify-center items-center">
      <n-breadcrumb-item  v-for="(route, index) in routeList" :key="index">
        <router-link v-if="index === 0" to="/apps">
          <span class="text-black dark:text-white text-2xl">
            {{ route }} 
          </span>
        </router-link>
        <div v-else>
          <span class="text-2xl">
            {{ route }} 
          </span>
        </div>
      </n-breadcrumb-item>
    </div>
  </n-breadcrumb>
</template>

<script setup lang="ts">
const routeName = computed(() => useRoute().name)
const routeList = computed(() => routeName.value.split('-'))

</script>
