<template>
    <app-navigator></app-navigator>
</template>

<script>
    import { createAppContainer, createStackNavigator } from 'vue-native-router';

    import MainScreen from './Main';
    import DetailScreen from './Details';
    import LoginScreen from './screens/Login';

    const StackNavigator = createStackNavigator(
        {
            Main: MainScreen,
            Details: DetailScreen,
            Login: LoginScreen,
        },
        {
            initialRouteName: 'Login',
        }
    );

    const AppNavigator = createAppContainer(StackNavigator);

    export default {
        components: { AppNavigator }
    }
</script>