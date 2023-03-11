<template>
    <div
        class="about-block"
        :style="{ backgroundImage: 'url(' + bgImage + ')' }"
    >
        <h3 class="about-block__title">
            {{ title }}
        </h3>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
    props: {
        title: String,
        bgImage: String,
    },
})
export default class extends Vue {}
</script>

<style scoped lang="scss">
.about-block {
    width: 376px;
    height: 450px;
    background-size: contain;
    background-repeat: no-repeat;
    padding: 0 20px;
    &__title {
        color: #fff;
        font-weight: 700;
        font-size: 27px;
        text-align: center;
        margin-top: 334px;
    }
}
</style>
