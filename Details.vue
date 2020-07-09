<template>
    <view>
        <text>{{ navigation.getParam('title') }}</text>
        <text>{{ navigation.getParam('imageSrc') }}</text>

        <image
                :style="{width: '100%', height: '100%'}"
                :source="{uri: navigation.getParam('imageSrc')}"
        />

        <button title="Back" :on-press="() => navigation.goBack()"/>
    </view>
</template>

<script>
    export default {
        // Declare `navigation` as a prop
        props: {
            navigation: {
                type: Object
            }
        },
        data() {
            return {
                title: '',
            }
        }
    }
</script>