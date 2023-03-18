<template>
    <div class="about-court-item">
        <img class="about-court-item__image" v-bind:src="image" alt="" />
        <p class="about-court-item__description">{{ description }}</p>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
    props: {
        image: String,
        description: String,
    },
})
export default class AboutCourtComponent extends Vue {
    description: any;
    image: string | undefined;
}
</script>

<style scoped lang="scss">
.about-court-item {
    width: 234px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 15px;
    &__description {
        font-weight: 700;
        font-size: 12px;
        color: #333333;
    }
}
</style>
