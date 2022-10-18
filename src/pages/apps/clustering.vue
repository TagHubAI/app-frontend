<script setup lang="ts">
import { useLoadingBar } from 'naive-ui'
const isProcessed = ref(false)
const isLoading = ref(false)
const loadingBar = useLoadingBar()

const getProcessedData = async () => {
  loadingBar.start()
  isLoading.value = true
  await new Promise(r => setTimeout(r, 500))
  isLoading.value = false
  loadingBar.finish()
  isProcessed.value = true
}
</script>

<template>
  <div class="flex justify-between">
    <!-- Data input form -->
    <div class="container w-1/4">
      <div class="text-lg text-black dark:text-white">
        Text data
      </div>
      <div class="color-gray-500" />
      <textarea id="message" rows="10" class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Your text data separate by line:&#10;&#10;Today is a nice day&#10;I don't feel so good today" />
      <div class="py-4 text-black dark:text-white">
        <n-button
          :loading="isLoading"
          class="bg-white dark:bg-black font-bold  px-4 rounded focus:outline-none focus:shadow-outline border border-black dark:border-white text-lg"
          type="button"
          @click="getProcessedData"
        >
          Process
        </n-button>
      </div>
    </div>
    <!-- Data analytics -->
    <div
      :class="{ 'bg-gray-100 dark:bg-coolGray-700 justify-center items-center': !isProcessed, 'bg-white': isProcessed }"
      class="flex container overflow-auto w-full max-h-150 text-lg text-middle rounded mx-4 border border-gray-300 align-middle "
    >
      <div v-if="!isProcessed">
        <span class="inline-block text-gray-500 align-middle">
          Your data will appear here
        </span>
      </div>
      <div v-else>
        <div class="container p-4 justify-center">
          <div class="grid grid-cols-4 grid-flow-row gap-4">
            <n-card title="">
              <span class="text-lg p-2">Group 1</span>
              <div class="p-2">
                <n-space>
                  <n-tag>Tag 1</n-tag>
                  <n-tag>Tag 2</n-tag>
                  <n-tag>Tag 3</n-tag>
                  <n-tag>Tag 4</n-tag>
                </n-space>
              </div>
              <n-collapse class="mt-4 bg-gray-100">
                <n-collapse-item title="Show example" name="1">
                  <div class="px-4">
                    This is an example
                    <br>This is an example
                    <br>This is an example
                    <br>This is an example
                    <br>This is an example
                    <br>This is an example
                    <br>This is an example
                    <br>This is an example
                    <br>This is an example
                  </div>
                </n-collapse-item>
              </n-collapse>
            </n-card>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

