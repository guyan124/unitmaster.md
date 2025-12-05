<script setup lang="ts">
  definePageMeta({
    layout: 'default'
  })

  const route = useRoute();

  const { data: page } = await useAsyncData(route.path, ()=> {
    return queryCollection('content').path(route.path).first();
  })

  const { data: surround } = await useAsyncData(`${route.path}-surround`, () => {
  return queryCollectionItemSurroundings('content', route.path)
})
</script>


<template>
  <UPage v-if="page">
     <UPageHeader headline="Unitmaster" :title="page.title" :description="page.description" />
    <UPageBody v-if="page.body">
       <ContentRenderer :value="page" />
       <USeparator />

      <UContentSurround :surround="surround" />
      
    </UPageBody>
    <template #right>
      <UPageCard>
     
        <UContentToc :links="page.body.toc?.links"/>
      </UPageCard>
    </template>
    

   
  </UPage>
</template>