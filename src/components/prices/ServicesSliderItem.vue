<template>
    <div class="item">
        <img :src="item.image" :alt="item.title" />
        <div class="item-title">{{ item.title }}</div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { ISliderItem } from "@/types/slider";

@Component({
    props: {
        item: {
            type: Object as () => ISliderItem,
            required: false,
        },
    },
})
export default class SevicesSliderItemComponent extends Vue {}
</script>

<style scoped lang="scss">
.item {
    min-width: 586px;
    position: relative;
    img {
        width: 100%;
    }
    &-title {
        font-weight: 700;
        font-size: 27px;
        color: #fff;
        position: absolute;
        bottom: 60px;
        left: 65px;
    }
}
</style>
