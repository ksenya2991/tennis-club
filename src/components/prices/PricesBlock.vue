<template>
    <div class="prices-and-services">
        <div class="prices-block">
            <h2 class="prices-block__title">Цены и абонементы</h2>
            <ButtonComponent
                v-for="(button, index) in buttons"
                :buttonContent="button.buttonContent"
                :key="index"
            />
        </div>
        <SevicesSliderComponent :items="services" />
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ButtonComponent from "./Button.vue";
import SevicesSliderComponent from "./ServicesSlider.vue";

@Component({
    components: {
        ButtonComponent,
        SevicesSliderComponent,
    },
})
export default class PricesBlockComponent extends Vue {
    buttons = [
        {
            buttonContent: "Зимний сезон 2021-2022",
        },
        {
            buttonContent: "Абонементы",
        },
        {
            buttonContent: "Скидки",
        },
        {
            buttonContent: "Дополнительные услуги",
        },
    ];
    services = [
        {
            image: require("@/assets/services-img.jpg"),
            title: "Уютное кафе",
        },
        {
            image: require("@/assets/services-img.jpg"),
            title: "Уютное кафе",
        },
        {
            image: require("@/assets/services-img.jpg"),
            title: "Уютное кафе",
        },
    ];
}
</script>

<style scoped lang="scss">
.prices-and-services {
    display: flex;
    justify-content: space-between;
    margin-top: 150px;
}
.prices-block {
    &__title {
        margin-bottom: 75px;
        font-weight: 700;
        font-size: 36px;
    }
}
</style>
