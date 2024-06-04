<script setup>
    import {ref, reactive, watchEffect, watch} from 'vue';
    import DynamicChild from './DynamicChild.vue';
    
    const emoji = ref("");
    const imgs = reactive({});
    const dynamicName1 = ref('');
    const dynamicName2 = ref('');
    watchEffect(async () => {
                        const response = await fetch("https://api.github.com/emojis");
                        const data = await response.json();
                        Object.assign(imgs, data);
                        console.log(imgs["100"]);
                    });
                    watch(dynamicName1, (newVal) => {
                        const url = imgs[newVal];
                        emoji.value = url;
                    });
</script>

<template>
    <div class="parentsContainer">
        <label>이모지 번호 입력하세요 : </label><input v-model="dynamicName1"/><br>
        <label>위치 입력하세요 : </label><input v-model="dynamicName2"/>

    
        <DynamicChild>
            <template #[dynamicName2]>
                <img :src="emoji">
            </template>
        </DynamicChild>
    </div>

</template>
<!-- 
    목표 : 입력받은 값을 화면에 이미지를 표시하고 그 이미지를 원하는 위치에 나타내게 함
    상황 : github에서 데이터를 요청하는 코드임

    1. 데이터 확인 : 외부 데이터 이미지 정보를 담는 데이터

    patents
    <html>
 
    2. 위치를 입력받을 input창 만들기
    3. 이모지 입력받는 인풋창 만들기
    4. 입력받은 이모지를 화면에 보여주기
    
    <sctipt>
    1. 반응성변수 인포트하기
    2. 위치입력받는 반응성 변수 생성
    3. 이모지 입력받는 반응성 변수 생성
    4. 입력받은 이모지를 불러오는 반응성변수 생성
    5. 이모지를 화면에 보여주기
    6. 슬롯으로 데이터 전송하기
    

    child
    1. 이미지 창 만들기
        - 이모지 입력창 옆에 보여줄 이미지창 변하는 값을 전달을 어떻게 하나??
        - 위치 입력시 동서남북으로 보여줄 이미지창 변하는 값을 전달을 어떻게 하나??
    


-->
<style scoped>
.parentsContainer {
    display: flex;
    align-items: center;
    flex-direction: column;
    border: 1px solid;
}
</style>