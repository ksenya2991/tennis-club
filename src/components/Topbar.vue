<template>
    <div id="Topbar">
        <ContainerComponent>
            <div class="topbar">
                <div class="topbar-logo">
                    <router-link to="/">
                        <img src="../assets/logo.svg" alt="" />
                    </router-link>
                </div>
                <div class="topbar-menu">
                    <MenuComponent />
                </div>
                <div class="topbar-socials">
                    <a href="http://youtube.com">
                        <img src="../assets/youtube.svg" alt="" />
                    </a>
                    <a href="http://vk.com">
                        <img src="../assets/vk.svg" alt="" />
                    </a>
                </div>
            </div>
        </ContainerComponent>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ContainerComponent from "@/components/Container.vue";
import MenuComponent from "./Menu.vue";

@Component({
    components: {
        ContainerComponent,
        MenuComponent,
    },
})
export default class extends Vue {}
</script>

<style scoped lang="scss">
#Topbar {
    border-bottom: 1px solid #ccc;
    position: absolute;
    width: 100%;
}
.topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 30px 0;
    &-menu {
        color: #fff;
    }
    &-socials {
        display: flex;
        align-items: center;
        a {
            margin-left: 10px;
        }
    }
}
</style>
