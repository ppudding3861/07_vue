<script setup="setup">
    import DynamicParent from './components/04_dynamicslot/DynamicParent.vue';
</script>

<template>
    <div>
        <h1>component Container</h1>
        <MyComponent/>
    </div>

    <main>
        <Parents/>
        
        <NamedParent/>

        <DynamicParent/>
    </main>
</template>

<style scoped="scoped">

</style>