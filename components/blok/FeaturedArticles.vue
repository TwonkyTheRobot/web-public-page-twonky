<template>
  <div v-editable="blok" style="overflow-x: clip" class="relative">
    <div
      class="bg-yellow-200 border-t-2 border-black absolute w-[120%] h-24 transform translate-x[-10%] rotate-3"
    ></div>
    <div
      class="bg-pink-300 border-t-2 border-black w-[120%] transform translate-x[-10%] -rotate-6"
    >
      <h2
        class="py-6 text-3xl sm:text-5xl text-black font-black font-display text-center"
      >
        {{ blok.title }}
      </h2>
    </div>

    <div class="max-w-5xl mt-16 mx-auto px-4 sm:px-6">
      <ul class="grid grid-cols-1 md:grid-cols-2 gap-6 md:gap-8 mb-8">
        <li
          v-for="(article, index) in sortedArticles"
          :key="article._uid"
          class="flex-auto transform"
          :class="[index % 2 ? '-rotate-1' : 'rotate-1']"
          style="min-width: 33%"
        >
          <ArticleTeaser
            v-if="article.content"
            :article-link="article.full_slug"
            :article-content="article.content"
          ></ArticleTeaser>

          <p v-else class="px-4 py-2 text-white bg-red-700 text-center rounded">
            This content loads on save.
            <strong>Save the entry & reload.</strong>
          </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
const props = defineProps({
  blok: {
    type: Object,
    required: true,
  },
});

const articles = useArticles();
const sortedArticles = computed(() => {
  const featuredArticles = articles.value;
      

      // Enable ordering of the article previews
      return featuredArticles.sort((a: any, b: any) => {
        return (
          props.blok.articles.indexOf(a.uuid) -
          props.blok.articles.indexOf(b.uuid)
        );
      });
});
</script>
