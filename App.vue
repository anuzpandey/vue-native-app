<template>
    <app-navigator></app-navigator>
</template>

<script>
    import { createAppContainer, createStackNavigator } from 'vue-native-router';

    import MainScreen from './Main';
    import DetailScreen from './Details';

    const StackNavigator = createStackNavigator(
        {
            Main: MainScreen,
            Details: DetailScreen,
        },
        {
            initialRouteName: 'Main',
        }
    );

    const AppNavigator = createAppContainer(StackNavigator);

    export default {
        components: { AppNavigator }
    }
</script>