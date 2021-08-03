<template>
  <section class="pt-128">
    <div class="container">
<!-- 
      <h2>{{ page.title }}</h2>
      <p>{{ page.description }}</p> -->
      <div class="flex items-start justify-between">
        <Aside :articles="pages" />
        <nuxt-content class="prose prose-sm sm:prose lg:prose-lg xl:prose-2xl mx-auto" :document="page"/>
        <Aside :articles="pages" />
      </div>
    </div>
  </section>
</template>

<script lang="js">
import Aside from '@/modules/docsSidebar.vue';
export default {
  components: {
    Aside
  },
  layout: 'docs',
  async asyncData({ $content, params }) {
    const slug = params.slug || "index";
    const page = await $content('docs', slug)
      .fetch();
    const pages = await $content('docs')
      .fetch();

    return {
      page,
      pages
    };
  },
};
</script>
