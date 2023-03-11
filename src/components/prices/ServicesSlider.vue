<template>
    <div class="services">
        <TitleComponent
            title="Услуги"
            :showControls="true"
            @arrowLeftClickHandler="clickOnLeft()"
            @arrowRightClickHandler="clickOnRight()"
        />
        <div class="services__slider">
            <div class="services__slider__line" ref="sliderItems">
                <SevicesSliderItemComponent
                    v-for="(item, index) in items"
                    :item="item"
                    :key="index"
                />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import TitleComponent from "../Title.vue";
import SevicesSliderItemComponent from "./ServicesSliderItem.vue";
import { ISliderItem } from "@/types/slider";

@Component({
    components: {
        TitleComponent,
        SevicesSliderItemComponent,
    },
    props: {
        items: {
            type: Array as () => ISliderItem[],
            required: false,
            default: [],
        },
    },
})
export default class SevicesSliderComponent extends Vue {
    itemWidth = 636;
    offset = 0;
    items: Array;
    clickOnLeft() {
        if (!this.offset) {
            return;
        }
        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
        this.offset = this.offset - this.itemWidth;
        listElement.style.transform = `translateX(${-this.offset}px)`;
    }
    clickOnRight() {
        if (this.offset >= 1272) {
            return;
        }
        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
        this.offset = this.offset + this.itemWidth;
        listElement.style.transform = `translateX(${-this.offset}px)`;
    }
}
</script>

<style scoped lang="scss">
.services {
    width: 636px;
    &__slider {
        border: 1px solid #f7ece1;
        overflow: hidden;
        padding: 30px 0 30px 25px;
        &__line {
            transition: 0.5s;
            display: flex;
            gap: 50px;
        }
    }
}
</style>
