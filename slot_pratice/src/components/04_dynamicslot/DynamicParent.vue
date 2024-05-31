<script setup>
    import {ref, reactive} from 'vue';
    import DynamicChild from './DynamicChild.vue';
    const imgs = ref(
     "https://search.pstatic.net/sunny/?src=https%3A%2F%2Fi.namu.wiki%2Fi%2FzkJqIWPidcqHAmOTLda13CnvLs8UZJGVx4C-Y2pa1jDdAx6GwX3t7buyuw-9vB3u7GN0tTIX2c8iXE7o_djj9w.webp&type=a340"
    );
    const dynamicName = ref('name');
</script>





<template>
    <div>
        <label>이모지 번호 입력하세요 : </label><input v-model="dynamicName"/><br>
        <label>위치 입력하세요 : </label><input v-model="dynamicName"/>
        <DynamicChild>
            <template #[dynamicName]>
                <img :src="imgs">
            </template>
        </DynamicChild>
    </div>

</template>

<style scoped>
    .parentsContainer {
        display: flex;
        align-items: center;
        flex-direction: column;
        border: 1px solid;
    }
</style>