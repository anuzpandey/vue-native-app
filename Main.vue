<template>
    <view class="container">
        <status-bar
                background-color="blue"
                bar-style="light-content"
        />
        <text class="text-color-primary">{{ myInput }}</text>

        <button title="Press Me!" @press="addExclamation"></button>
        <button title="Details Page" @press="detailsPage"></button>

        <view :style="{borderTopWidth: 1, borderTopColor: 'gray', width: '100%'}"></view>

        <scroll-view :style="{width: '100%'}">
            <view class="border" v-for="(post, index) in posts" :key="index">
                <touchable-opacity class="flex-container" :on-press="() => handleListTap(post)">
                    <image
                            :style="{width: 40, height: 40, borderRadius: 25, marginRight: 8}"
                            :source="{uri: post.data.thumbnail}"
                    />
                    <text>{{ post.data.title }}</text>
                </touchable-opacity>
            </view>
        </scroll-view>
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
        mounted() {
            fetch('https://reddit.com/r/aww.json')
                .then(response => response.json())
                .then(data => {
                    this.posts = data.data.children
                });
        },
        data() {
            return {
                myInput: "Apple",
                posts: [],
            };
        },
        methods: {
            addExclamation: function () {
                this.myInput += "!";
            },
            detailsPage: function () {
                this.navigation.navigate("Details");
            },
            handleListTap: function(post) {
                // console.log(post.data.title);
                this.navigation.navigate("Details", {
                    imageSrc: post.data.preview.images[0].source.url,
                    title: post.data.title,
                })
            }
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

    .border {
        border-bottom-width: 1;
        border-color: gray;
        width: 100%;
        padding: 15;
    }
    .flex-container {
        flex-direction: row;
        align-items: center;
    }
</style>
