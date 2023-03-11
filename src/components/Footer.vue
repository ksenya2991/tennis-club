<template>
    <div class="footer">
        <Container :style-type="containerType.FLEX_JUSTIFY_BETWEEN">
            <div class="footer-copyright">2022 © Все права защищены.</div>
            <MenuComponent text-color="#000" />
            <div class="footer-socials">
                <a href="http://youtube.com">
                    <YouTubeComponent fill="#8D86C9" />
                </a>
                <a href="http://vk.com">
                    <VkComponent fill="#8D86C9" />
                </a>
                <a href="http://telegram.org">
                    <img src="../assets/telegram-footer.svg" alt="" />
                </a>
            </div>
        </Container>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Container from "@/components/Container.vue";
import MenuComponent from "./Menu.vue";
import { ContainerType } from "@/components/Container.vue";
import YouTubeComponent from "./ui/YouTube.vue";
import VkComponent from "./ui/Vk.vue";

@Component({
    components: {
        Container,
        MenuComponent,
        YouTubeComponent,
        VkComponent,
    },
})
export default class FooterComponent extends Vue {
    containerType = ContainerType;
}
</script>

<style scoped lang="scss">
.footer {
    background-color: #f7ece1;
    padding: 38px 0;
    margin-top: 150px;
    &-copyright {
        font-weight: 500;
        font-size: 14px;
        color: rgba(51, 51, 51, 0.3);
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
