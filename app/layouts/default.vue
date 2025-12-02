<script setup lang="ts">
const { data: navigation } = await useAsyncData('nav', ()=> {
    return queryCollectionNavigation('content')
})

</script>

<template>
 <UPage>

    <template #default>
        <slot/>
    </template>

    <template #left>
        <UPageAside>
            <UContentNavigation :navigation="navigation"/>
        </UPageAside>
    </template>
 </UPage>   
</template>