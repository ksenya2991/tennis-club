<template>
    <div class="title-wrapper">
        <h3 class="title">{{ title }}</h3>
        <div class="title-controls" v-if="showControls">
            <button :disabled="disabledLeft" @click="arrowLeftClickHandler()">
                <img src="../assets/arrow-left.svg" alt="" />
            </button>
            <button :disabled="disabledRight" @click="arrowRightClickHandler()">
                <img src="../assets/arrow-right.svg" alt="" />
            </button>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
    props: {
        title: {
            type: String,
            required: true,
        },
        showControls: {
            type: Boolean,
            required: false,
        },
        disabledLeft: {
            type: Boolean,
            default: false,
        },
        disabledRight: {
            type: Boolean,
            default: false,
        },
    },
})
export default class TitleComponent extends Vue {
    showControls: unknown;
    title: unknown;
    disabledRight: boolean | undefined;
    disabledLeft: boolean | undefined;
    arrowLeftClickHandler() {
        this.$emit("arrowLeftClickHandler");
    }
    arrowRightClickHandler() {
        this.$emit("arrowRightClickHandler");
    }
}
</script>

<style scoped lang="scss">
.title-wrapper {
    margin-bottom: 75px;
    display: flex;
    justify-content: space-between;
}

.title {
    font-size: 36px;
    font-weight: 700;
}
.title-controls {
    button {
        background-color: #8d86c9;
        border: none;
        width: 45px;
        height: 45px;
        margin-left: 15px;
        cursor: pointer;
        &:hover {
            background-color: #807ab7;
        }
    }
}
button[disabled] {
    opacity: 0.5;
}
</style>
