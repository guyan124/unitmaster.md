
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
          <div class="content-area">
          <ContentRenderer v-if="page" :value="page"></ContentRenderer>
          <p v-else>No content</p>
          </div>
        </UPageBody>
         <template #right>
           <div class="toc-right"> 
            <h1>TOC</h1>
             <ul>
          <li><a href="#securities/fund">Securities/Fund</a></li>
          <li><a href="#section2">Overview</a></li>
          <li><a href="#section3">Section 3</a></li>
        </ul>
        </div> 
         </template>
    </UPage>
   
</template>



