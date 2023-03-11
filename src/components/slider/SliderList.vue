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
import TitleComponent from "../Title.vue";

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
            default: "title",
        },
        itemCountToShow: {
            type: Number,
            required: true,
            default: 1,
        },
    },
})
export default class SliderListComponent extends Vue {
    offset = 0;
    sliderItemWidth = 0;
    gapCssProp = 0;
    maxSliderLineWidth = 0;
    title: any;

    mounted() {
        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
        this.sliderItemWidth = listElement.children[0].clientWidth;
        const gapCssProp = window
            .getComputedStyle(listElement, null)
            .getPropertyValue("gap");
        this.gapCssProp = parseInt(gapCssProp);
        this.maxSliderLineWidth =
            this.sliderItemWidth *
                (listElement.children.length - this.$props.itemCountToShow) -
            this.sliderItemWidth;

        console.log(this.sliderItemWidth * listElement.children.length);
    }
    clickOnLeft() {
        if (!this.offset) {
            return;
        }
        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
        this.offset = this.offset - (this.gapCssProp + this.sliderItemWidth);
        listElement.style.transform = `translateX(${-this.offset}px)`;
    }
    clickOnRight() {
        console.log("this.offset", this.offset);
        console.log("this.maxSliderLineWidth", this.maxSliderLineWidth);

        if (this.offset >= this.maxSliderLineWidth) {
            return;
        }
        const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
        this.offset = this.offset + (this.gapCssProp + this.sliderItemWidth);
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
