<template>
    <div class="container" :class="styleType">
        <template>
            <slot> </slot>
        </template>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

export enum ContainerType {
    GRID = "grid",
    FLEX_JUSTIFY_BETWEEN = "flex-justify-between",
    GRID_NEWS = "grid-news",
}

@Component({
    props: {
        styleType: String as () => ContainerType,
    },
})
export default class extends Vue {
    styleType: string | undefined;
}
</script>

<style scoped lang="scss">
.container {
    width: 1200px;
    margin: 0 auto;
}
.container.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 12px;
}
.container.flex-justify-between {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.container.grid-news {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 24px;
}
</style>
