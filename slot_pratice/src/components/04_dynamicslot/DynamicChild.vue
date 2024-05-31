<script setup="setup"></script>

<template>
    <div class="container">
        <div class="north">
            <slot name="north"></slot>
        </div>
        <div class="container-sub">
            <div class="east">
                <slot name="east"></slot>
            </div>
            <div class="west">
                <slot name="west"></slot>
            </div>
        </div>
        <div class="south">
            <slot name="south"></slot>
        </div>
    </div>
</template>

<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 1500px;
        height: 3000px;

    }
    .container-sub{
        display: flex;
        flex-direction: row;
        align-items: center;
        padding: 30px;
    }

    .north {
        width: 200px;
        height: 200px;

    }

    .south {
        width: 200px;
        height: 200px;

  
    }

    .east {
        width: 200px;
        height: 200px;

    padding: 30px;
    }

    .west {
        width: 200px;
        height: 200px;

    padding: 30px;
    margin-left: 500px;
    }
</style>