
<script setup lang="ts">
import { container } from '#build/ui';

 const { data: navigation } = await useAsyncData('nav', ()=> {
    return queryCollectionNavigation('content')
})
</script>


<template>
  <UPage>
    <template #left>
      <UPageAside>
        <UContentNavigation :navigation="navigation"/>
      </UPageAside>
    </template>

    <UPageBody>
      <slot/>
    </UPageBody>    
    
  </UPage>
  
</template>
