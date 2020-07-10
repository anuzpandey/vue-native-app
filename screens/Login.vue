<template>
    <view class="flex-container">

        <view
                :style="{width: 300, height: 'auto', borderRadius: 12, shadow: 10, backgroundColor: 'white', alignItems: 'center', padding: 24}"
        >
            <image
                    :style="{width: 119, height: 100, marginBottom: 12}"
                    :source="{uri: 'http://www.kathmandu.gov.np/sites/all/themes/newmun/new_logo.png'}"
            />

            <view>
                <text :style="{fontSize: 24, textAlign: 'center', fontWeight: 'bold'}">LOGIN</text>
                <view class="p-12">
                    <text-input type="text" placeholder="Username" v-model="username" class="textInput"/>
                    <text :style="{color: 'red', fontSize: 8}">{{ errorUsername }}</text>
                </view>
                <view class="p-12 mb-24">
                    <text-input type="password" placeholder="Password" v-model="password"/>
                    <text :style="{color: 'red', fontSize: 8}">{{ errorPassword }}</text>
                </view>
                <button
                        :on-press="loginAction"
                        title="Sign In"
                />
            </view>
        </view>

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
            username: '',
            password: '',
            errorUsername: '',
            errorPassword: '',
        };
    },
    methods: {
        loginAction: function () {
            if (this.username === '') {
                this.errorUsername = "Please Enter your Username";
            } else if (this.password === '') {
                this.errorPassword = "Please Enter your Password";
            } else {
                if (this.username !== 'admin' && this.password !== 'password') {
                    alert('Wrong Username or Password');
                } else {
                    this.navigation.navigate('Main')
                }
            }
        }
    }
}

</script>

<style>
    .flex-container {
        background-color: #fafafa;
        align-items: center;
        justify-content: center;
        flex: 1;
    }

    .p-12 {
        padding: 12;
    }

    .textInput {
        width: 250;
    }

    .mb-24 {
        margin-bottom: 24;
    }

</style>