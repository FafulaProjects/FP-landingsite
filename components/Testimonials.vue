<script setup>
  const props = defineProps({
    title: String,
    description: String,
    items: Array
  });
</script>

<template>
  <h2 class="text-3xl font-bold text-center text-zinc-800 sm:text-4xl" v-if="title">
    {{ title }}
  </h2>

  <p class="max-w-3xl mx-auto mt-4 text-lg text-center text-zinc-600" v-if="description">
    {{ description }}
  </p>

  <!-- HORIZONTAL SCROLLER -->
  <div
    class="mt-10 mb-20 overflow-x-auto pb-6"
  >
    <div class="flex gap-6 w-max px-2">
      <blockquote
        v-for="item in items"
        :key="item.author?.name"
        class="w-80 p-6 border-2 border-dashed rounded-sm border-zinc-300 bg-white shadow-sm flex-shrink-0"
      >
        <p class="text-zinc-500" v-if="item.quote">
          {{ item.quote }}
        </p>

        <footer class="flex items-center gap-4 mt-4" v-if="item.author">
          <NuxtImg
            :src="item.author.avatar"
            :alt="item.author.name"
            width="64"
            height="64"
            class="object-cover w-16 h-16 rounded-sm shrink-0"
            v-if="item.author.avatar"
          />
          <div class="text-sm">
            <p class="font-bold text-zinc-800">
              {{ item.author.name }}
            </p>
            <p class="text-zinc-500">
              {{ item.author.title }}
            </p>
          </div>
        </footer>
      </blockquote>
    </div>
  </div>
</template>
