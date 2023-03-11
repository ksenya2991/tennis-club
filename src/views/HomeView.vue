<template>
    <div class="home">
        <header class="home-header">
            <ContainerComponent>
                <h1 class="home-header__title">
                    Петербургский <br />
                    теннисный клуб <br />
                    имени М.А. Пасечникова
                </h1>
            </ContainerComponent>
            <ContainerComponent :style-type="containerType.GRID">
                <ServiceBlockComponent
                    v-for="(service, index) in services"
                    :service-block="service"
                    :key="index"
                />
            </ContainerComponent>
        </header>
        <section class="about-blocks">
            <AboutBlockComponent
                v-for="(block, index) in aboutBlocks"
                :title="block.title"
                :bg-image="block.bgImage"
                :key="index"
            />
        </section>
        <section class="sport-club">
            <ContainerComponent>
                <BoardComponent
                    title="Спортивный клуб"
                    :imageUrl="require('@/assets/about-sport-club.jpg')"
                />
            </ContainerComponent>
        </section>
        <section class="coaches">
            <ContainerComponent>
                <SliderListComponent
                    title="Тренерский состав"
                    :itemCountToShow="5"
                >
                    <div
                        class="coaches"
                        v-for="(item, index) in coaches"
                        :key="index"
                    >
                        <div class="coaches-item">
                            <img :src="item.image" :alt="item.title" />
                            <div class="coaches-item-title">
                                {{ item.title }}
                            </div>
                            <div class="coaches-item-description">
                                {{ item.description }}
                            </div>
                        </div>
                    </div>
                </SliderListComponent>
            </ContainerComponent>
        </section>
        <section class="prices-servises">
            <ContainerComponent>
                <PricesBlockComponent />
            </ContainerComponent>
        </section>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ContainerComponent from "@/components/Container.vue";
import ServiceBlockComponent from "@/components/ServiceBlock.vue";
import { IServiceBlock } from "@/types/serviceBlock";
import { ContainerType } from "@/components/Container.vue";
import AboutBlockComponent from "@/components/AboutBlock.vue";
import SliderListComponent from "@/components/slider/SliderList.vue";
import PricesBlockComponent from "@/components/prices/PricesBlock.vue";
import BoardComponent from "@/components/Board.vue";

@Component({
    components: {
        ContainerComponent,
        ServiceBlockComponent,
        AboutBlockComponent,
        SliderListComponent,
        PricesBlockComponent,
        BoardComponent,
    },
})
export default class HomeView extends Vue {
    containerType = ContainerType;
    services: IServiceBlock[] = [
        {
            title: "Услуги",
            description: "Аренда корта",
            link: "/",
        },
        {
            title: "Услуги",
            description: "Детский теннис",
            link: "/",
        },
        {
            title: "Услуги",
            description: "Сборы команд",
            link: "/",
        },
        {
            title: "Услуги",
            description: "Расписание",
            link: "/",
        },
    ];
    aboutBlocks = [
        {
            title: "5 летних грунтовых кортов",
            bgImage: require("../assets/girl.jpg"),
        },
        {
            title: "Зал с покрытием “Искусственная трава”",
            bgImage: require("../assets/ball.jpg"),
        },
        {
            title: "Зал с покрытием “Хард”",
            bgImage: require("../assets/balls.jpg"),
        },
    ];
    coaches = [
        {
            image: require("@/assets/coach-1.jpg"),
            title: "Pulvinar aliquam",
            description:
                "Arcu elit massa amet turpis vel consequat pellentesque sit.",
        },
        {
            image: require("@/assets/coach-2.jpg"),
            title: "Pretium odio",
            description:
                "Bibendum aliquam volutpat nisl a duis in nisi. In sed commodo lorem morbi quis.",
        },
        {
            image: require("@/assets/coach-3.jpg"),
            title: "Aliquet consectetur",
            description:
                "Id sapien sed nibh fermentum massa posuere ipsum. Diam in.",
        },
        {
            image: require("@/assets/coach-4.jpg"),
            title: "Blandit augue",
            description:
                "Scelerisque accumsan pretium justo, vitae elit. Dolor semper morbi sit auctor vel diam eros.",
        },
        {
            image: require("@/assets/coach-5.jpg"),
            title: "Lorem lacus",
            description:
                "Adipiscing amet, viverra dignissim egestas. Sed nibh egestas venenatis faucibus.",
        },
        {
            image: require("@/assets/coach-6.jpg"),
            title: "Sed erat",
            description:
                "Quis ullamcorper pretium lacus risus tellus dolor etiam.",
        },
        {
            image: require("@/assets/coach-1.jpg"),
            title: "Pulvinar aliquam",
            description:
                "Arcu elit massa amet turpis vel consequat pellentesque sit.",
        },
        {
            image: require("@/assets/coach-2.jpg"),
            title: "Pretium odio",
            description:
                "Bibendum aliquam volutpat nisl a duis in nisi. In sed commodo lorem morbi quis.",
        },
        {
            image: require("@/assets/coach-3.jpg"),
            title: "Aliquet consectetur",
            description:
                "Id sapien sed nibh fermentum massa posuere ipsum. Diam in.",
        },
        {
            image: require("@/assets/coach-4.jpg"),
            title: "Blandit augue",
            description:
                "Scelerisque accumsan pretium justo, vitae elit. Dolor semper morbi sit auctor vel diam eros.",
        },
        {
            image: require("@/assets/coach-5.jpg"),
            title: "Lorem lacus",
            description:
                "Adipiscing amet, viverra dignissim egestas. Sed nibh egestas venenatis faucibus.",
        },
        {
            image: require("@/assets/coach-6.jpg"),
            title: "Sed erat",
            description:
                "Quis ullamcorper pretium lacus risus tellus dolor etiam.",
        },
    ];
}
</script>

<style lang="scss" scoped>
.home-header {
    background-image: url("../assets/header-bg.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    padding-top: 200px;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    &__title {
        color: #fff;
        font-weight: bold;
        font-size: 40px;
    }
}
.about-blocks {
    width: 1250px;
    margin: auto;
    margin-top: 150px;
    margin-bottom: 150px;
    display: flex;
    justify-content: space-between;
}

.sport-club {
    margin-bottom: 150px;
}
.coaches-item {
    min-width: 166px;
    text-align: center;
    img {
        width: 100%;
    }
    &-title {
        height: 50px;
        font-size: 21px;
        font-weight: 600;
        margin-top: 25px;
        margin-bottom: 15px;
    }
    &_description {
        font-size: 10px;
        font-weight: 400;
    }
}
</style>
