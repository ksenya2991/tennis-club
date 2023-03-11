<template>
    <div id="app">
        <TopbarComponent />
        <router-view></router-view>
        <FooterComponent />
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ContainerComponent from "@/components/Container.vue";
import TopbarComponent from "@/components/Topbar.vue";
import FooterComponent from "./components/Footer.vue";

@Component({
    components: {
        ContainerComponent,
        TopbarComponent,
        FooterComponent,
    },
})
export default class App extends Vue {}
</script>

<style lang="scss">
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    font-family: sans-serif;
    width: 100%;
}

ul {
    list-style: none;
}

a {
    text-decoration: none;
}
</style>
