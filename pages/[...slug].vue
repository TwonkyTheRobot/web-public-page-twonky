<template>
<NuxtLayout name="default">
  <component
    v-if="story?.content.component"
    :is="story.content.component"
    :key="story.content._uid"
    :blok="story.content"
    :story="story"
  />
  </NuxtLayout>
</template>

<script lang="ts" setup>
import { useStoryblokApi, useStoryblokBridge } from "@storyblok/vue";
const route = useRoute();


// fetch the story before rendering the page ('usally at the server')
const slug = route.params.slug;
const path = `cdn/stories/${Array.isArray(slug)? slug.join('/'): ((!slug || slug == '') ? 'home' : slug)}`
console.log('PATHMATCH', path);
// fetch the story before rendering the page ('usally at the server')
const storyblokApi = useStoryblokApi();
const { data: story } = await useAsyncData(path, async () => {
  const { data } = await storyblokApi.get(path, {
    version: "draft",
  });
  return data.story;
});

// enable bridge for WYSIWYG integration
onMounted(() => {
  useStoryblokBridge(
    story.value?.id,
    (newStory) => (story.value = newStory)
  );
});
</script>
