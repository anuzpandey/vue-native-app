<template>
    <view class="container">
        <status-bar
                background-color="blue"
                bar-style="light-content"
        />
        <text class="text-color-primary">{{ myInput }}</text>

        <button title="Press Me!" @press="addExclamation"></button>
    </view>
</template>

<script>
    export default {
        data() {
            return {
                myInput: "",
            };
        },
        methods: {
            addExclamation: function () {
                this.message += "!";
            },
        },
    };
</script>

<style>
    .container {
        background-color: white;
        align-items: center;
        justify-content: center;
        flex: 1;
    }

    .text-color-primary {
        padding: 10px;
        font-size: 16px;
        color: blue;
    }

    .p15 {
        padding: 15;
    }
</style>
