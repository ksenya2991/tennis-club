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
                >
                    <p>
                        Imperdiet lorem ipsum, pulvinar aliquet sit ultricies in
                        sit turpis. Ultricies erat pretium risus quam tincidunt
                        non viverra porttitor. Sollicitudin enim nunc in nisi
                        donec vel. Blandit mauris vitae amet aliquet ultrices
                        mauris pellentesque. Non ipsum commodo, sit mi sit netus
                        aenean nisl. Donec sit pellentesque enim, vestibulum.
                    </p>
                    <br />
                    <p>
                        Condimentum hac adipiscing purus in augue nisi.
                        Convallis ut nisi.
                    </p>
                    <br />
                    <h3>Ornare orci ut dictum nulla fames.</h3>
                    <ul>
                        <li>
                            Euismod diam, vel venenatis bibendum sodales sem
                            hendrerit vulputate sagittis.
                        </li>
                        <li>
                            Nisl senectus sed malesuada donec. Interdum
                            malesuada bibendum imperdiet elementum auctor vitae
                            in.
                        </li>
                        <li>
                            Quam purus ornare dictum pharetra. Sed viverra
                            tellus sollicitudin urna, sagittis.
                        </li>
                        <li>
                            Scelerisque urna senectus commodo, nam. Donec nibh
                            tempus imperdiet nisi, tincidunt mus egestas nisl
                            nullam.
                        </li>
                    </ul>
                </BoardComponent>
            </ContainerComponent>
        </section>
        <section class="coaches">
            <ContainerComponent>
                <SliderListComponent
                    title="Тренерский состав"
                    :itemCountToShow="6"
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
import ContainerComponent from "../components/Container.vue";
import ServiceBlockComponent from "../components/ServiceBlock.vue";
import { IServiceBlock } from "../types/serviceBlock";
import { ContainerType } from "../components/Container.vue";
import AboutBlockComponent from "../components/AboutBlock.vue";
import SliderListComponent from "../components/slider/SliderList.vue";
import PricesBlockComponent from "../components/prices/PricesBlock.vue";
import BoardComponent from "../components/Board.vue";

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
    p {
        font-weight: 400;
        font-size: 14px;
        color: #333333;
    }
    h3 {
        font-weight: 600;
        font-size: 21px;
        margin-bottom: 30px;
        margin-top: 30px;
    }
    li {
        font-weight: 400;
        font-size: 14px;
        padding-bottom: 20px;
        margin-left: 23px;
        position: relative;
        &:before {
            content: "";
            display: block;
            width: 8px;
            height: 8px;
            background-color: #8d86c9;
            border: none;
            position: absolute;
            left: -23px;
            top: 3px;
        }
    }
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
