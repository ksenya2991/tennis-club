<template>
    <div class="slider-wrapper">
        <TitleComponent
            :title="title"
            :showControls="true"
            @arrowLeftClickHandler="clickOnLeft()"
            @arrowRightClickHandler="clickOnRight()"
        />
        <div class="slider-items">
            <div class="slider-items-line" ref="sliderItems">
                <template>
                    <slot></slot>
                </template>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { ISliderItem } from "@/types/slider";
import TitleComponent from "@/components/Title.vue";

@Component({
    components: {
        TitleComponent,
    },
    props: {
        items: {
            type: Array as () => ISliderItem[],
            required: false,
            default: () => [],
        },
        title: {
            type: String,
            default: "Title",
        },
        itemCountToShow: {
            type: Number,
            default: 1,
        },
    },
})
export default class SliderListComponent extends Vue {
    offset = 0;
    sliderItemWidth = 0;
    gapCssProp = 0;
    maxSliderLineWidth = 0;

    mounted() {
        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
        this.sliderItemWidth = listElement.children[0].clientWidth;
        this.maxSliderLineWidth =
            this.sliderItemWidth *
                (listElement.children.length -
                    (this.$props.itemCountToShow - 1)) -
            this.sliderItemWidth;

        const gapCssProp = window
            .getComputedStyle(listElement, null)
            .getPropertyValue("gap");

        this.gapCssProp = parseInt(gapCssProp);
    }

    clickOnLeft() {
        if (this.offset >= this.maxSliderLineWidth) {
            return;
        }

        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
        this.offset = this.offset + (this.gapCssProp + this.sliderItemWidth);

        listElement.style.transform = `translateX(${-this.offset}px)`;
    }

    clickOnRight() {
        if (!this.offset) {
            return;
        }
        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;

        this.offset = this.offset - (this.gapCssProp + this.sliderItemWidth);
        listElement.style.transform = `translateX(${-this.offset}px)`;
    }
}
</script>

<style scoped lang="scss">
.slider-wrapper {
    margin-top: 30px;
}
.slider-items {
    overflow: hidden;
}
.slider-items-line {
    transition: 0.3s;
    display: flex;
    gap: 37px;
}
</style>
