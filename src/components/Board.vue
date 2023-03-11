<template>
    <div class="board">
        <!-- <img :src="imageUrl" class="left-image" /> -->
        <div
            class="right-info"
            :style="{ '--bgImage': 'url(' + imageUrl + ')' }"
        >
            <div class="right-info__title">{{ title }}</div>
            <template>
                <slot></slot>
            </template>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
    props: {
        imageUrl: {
            type: String,
            default: "",
        },
        title: {
            type: String,
            default: "title",
        },
    },
})
export default class BoardComponent extends Vue {}
</script>

<style scoped lang="scss">
.board {
    position: relative;
    display: flex;
    justify-content: flex-end;
}
// .left-image {
//     position: absolute;
//     width: 526px;
// }
.right-info {
    padding: 40px 60px 0 146px;
    position: relative;
    background-color: #f7ece1;
    max-width: 850px;
    height: 654px;
    &::before {
        content: "";
        display: block;
        background-image: var(--bgImage);
        background-repeat: no-repeat;
        position: absolute;
        width: 526px;
        height: 514px;
        left: -50%;
    }
    &__title {
        font-weight: 700;
        font-size: 36px;
        margin-bottom: 40px;
    }
}
</style>
