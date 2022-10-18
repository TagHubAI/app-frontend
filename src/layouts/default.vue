<template>
  <main class="dark:text-gray-200">
  <div class="flex text-white bg-black text-xl justify-between">
    <span class="text-white mx-4 my-4 ">
      <router-link to="/apps">
        TagHub.Dev 
      </router-link>
    </span>
    <span class="mx-4 my-4">
      <div class="flex">
        <div class="inline-block">
          <button class="icon-btn mx-2 !outline-none" :title="t('button.toggle_dark')" @click="toggleDark()">
            <div i="carbon-sun dark:carbon-moon" />
          </button>
          <span>
            Patrick (Credit left: 10000)
          </span>
          <n-button class="text-white" :loading="loading" icon-placement="left" @click="handleClick">
              Log out
          </n-button>
        </div>
      </div>
    </span>
  </div>
  <div class="px-6 py-6">
    <Breadcrumb />
    <div class="px-4 py-4">
      <RouterView />
    </div>
  </div>
  </main>
</template>

<style>

.full-height {
  height: 100vh;
  max-height: 100vh;
  min-height: -moz-available;
  min-height: -webkit-fill-available;
  min-height: fill-available;
}
</style>
<script setup lang="ts">
  const { t, availableLocales, locale } = useI18n()
  const toggleLocales = () => {
    // change to some real logic
    const locales = availableLocales
    locale.value = locales[(locales.indexOf(locale.value) + 1) % locales.length]
  }
</script>
