<template>
  <Generator>
    <p class="text-center text-4xl leading-normal">
      {{ data.text }}
    </p>

    <div class="flex justify-center">
      <button
        class="bg-gray-900 text-white px-4 py-2 rounded-md mt-4"
        @click="copy"
      >
        {{ button }}
      </button>
    </div>

    <div class="rounded-xl border border-gray-300 mt-10 py-5">
      <p class="text-center text-xl">カスタマイズ</p>

      <form class="px-5" @change="generate">
        <div class="my-3">
          <label
            for="author"
            class="block text-sm font-medium leading-6 text-gray-900"
          >
            名前
          </label>
          <div class="mt-2">
            <input
              id="author"
              type="text"
              class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
              v-model="data.author"
            />
          </div>
        </div>

        <div class="my-3">
          <label
            for="time1"
            class="block text-sm font-medium leading-6 text-gray-900"
          >
            時間1
          </label>
          <div class="mt-2">
            <input
              id="time1"
              type="text"
              class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
              v-model="data.time1"
            />
          </div>
        </div>

        <div class="my-3">
          <label
            for="time2"
            class="block text-sm font-medium leading-6 text-gray-900"
          >
            時間2
          </label>
          <div class="mt-2">
            <input
              id="time2"
              type="text"
              class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
              v-model="data.time2"
            />
          </div>
        </div>

        <div class="my-3">
          <label
            for="zenka"
            class="block text-sm font-medium leading-6 text-gray-900"
          >
            前科持ち
          </label>
          <div class="mt-2">
            <input
              id="zenka"
              type="text"
              class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
              v-model="data.zenka"
            />
          </div>
        </div>
      </form>
    </div>
  </Generator>
</template>

<script setup>
import Generator from "~/layouts/Generator.vue";

const data = reactive({
  text: "",
  author: "太郎",
  time1: "9",
  time2: "20:00",
  zenka: "次郎",
});

const button = ref("コピー");

onMounted(generate);

function generate() {
  data.text = `${data.author}「${data.time1}時集合でいい？結局${data.time2}からでもいいけど${data.zenka}に前科あるしやばい」`;
}

function copy() {
  navigator.clipboard.writeText(data.text);

  button.value = "コピーしました";
  setTimeout(() => {
    button.value = "コピー";
  }, 1500);
}
</script>
