
<script lang="ts"   setup>
  const route = useRoute();
  const { data: page } = await useAsyncData(route.path, () => {
    return queryCollection('content').path(route.path).first()
  })
</script>


<template>
    <UPage>
        <UPageHeader></UPageHeader>
        <UPageBody>
          <ContentRenderer v-if="page" :value="page"></ContentRenderer>
        </UPageBody>
         <template #right>
            <h1>TOC</h1>
         </template>
    </UPage>
   
</template>