<template>
    <div class="service-block">
        <h4 class="service-block__title">
            {{ serviceBlock.title }}
        </h4>
        <div class="service-block__subtitle">
            <h4 class="service-block__description">
                {{ serviceBlock.description }}
            </h4>
            <a :href="serviceBlock.link">
                <img src="../assets/link-more.svg" alt="" />
            </a>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { IServiceBlock } from "@/types/serviceBlock";

@Component({
    props: {
        serviceBlock: Object as () => IServiceBlock,
    },
})
export default class extends Vue {}
</script>

<style scoped lang="scss">
.service-block {
    background-color: #8d86c9;
    color: #ffffff;
    padding: 30px;
    &__title {
        margin-bottom: 10px;
        font-size: 15px;
    }
    &__subtitle {
        display: flex;
        align-items: center;
        gap: 55px;
        transition: 0.3s;
        a {
            img:hover {
                transform: scale(1.2);
            }
        }
    }
    &__description {
        font-size: 18px;
    }
}
</style>
