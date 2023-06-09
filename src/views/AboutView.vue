<template>
    <div>
        <header class="about-header">
            <h2 class="about-header__title">О клубе</h2>
        </header>
        <section class="about-photos">
            <Container>
                <SliderListComponent title="Фото кортов">
                    <div
                        class="about-slide-item"
                        v-for="(photo, index) in courtPhotos"
                        :key="index"
                        :style="{
                            backgroundImage:
                                'url(' + photo.backgroundImgUrl + ')',
                        }"
                    >
                        <router-link
                            tag="a"
                            to="photo.routeUrl"
                            class="about-slide-item__btn"
                        >
                            {{ photo.routeTitle }}
                        </router-link>
                    </div>
                </SliderListComponent>
            </Container>
        </section>
        <section class="about-board">
            <Container>
                <h2 class="about-title">О клубе</h2>
                <BoardComponent
                    title="Петербургский теннисный клуб имени М.А. Пасечникова"
                    :imageUrl="require('@/assets/left-img-board.jpg')"
                >
                    <p class="board-text">
                        Feugiat gravida proin arcu tellus ipsum posuere nisl,
                        consectetur scelerisque. Posuere ipsum tellus dignissim
                        etiam lorem ultrices risus viverra. Purus volutpat
                        phasellus viverra vestibulum quis. Gravida pretium odio
                        enim ut id tempus semper. Urna cum at in iaculis mauris
                        at. Tellus, a euismod tincidunt eu orci faucibus. Mi
                        faucibus pellentesque molestie nunc, et, tellus. Neque
                        cras mattis dolor id. Maecenas vivamus tristique donec
                        neque id convallis. Feugiat fusce at est at.
                    </p>
                    <br />
                    <p class="board-text">
                        Vitae nec eget blandit id nisl. Sit ac dictum lorem
                        mauris posuere sit. Gravida commodo egestas pharetra, mi
                        interdum. Ullamcorper pulvinar hac risus egestas fusce
                        nunc. Vel auctor proin integer ut lacus, sed neque id
                        dictum. At enim quis eu, mattis aliquet varius in eu
                        venenatis.
                    </p>
                    <br />
                    <p class="board-text">
                        Quisque diam elit donec orci sed dolor. Neque sed sit
                        tortor eget urna magna interdum feugiat ut. In purus
                        rhoncus egestas euismod morbi. Ut velit facilisi in cras
                        tempus turpis sapien ipsum, mattis. Tempor sit nulla ac
                        lorem placerat congue. Nulla purus vestibulum suscipit
                        pellentesque risus non.
                    </p>
                    <div class="about-board__details">
                        <AboutCourtComponent
                            v-for="(item, index) in courts"
                            :description="item.description"
                            :image="item.image"
                            :key="index"
                        />
                    </div>
                </BoardComponent>
            </Container>
        </section>
        <section class="rules">
            <container>
                <TitleComponent title="Правила" />
            </container>
            <container :styleType="containerType.FLEX">
                <div class="about-sidebar">
                    <AboutRuleComponent
                        v-for="(rule, index) in rulesList"
                        :key="index"
                        :rule="rule"
                        :numberOfRule="index + 1"
                    />
                </div>
                <div class="about-views">
                    <router-view />
                </div>
            </container>
        </section>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Container from "../components/Container.vue";
import SliderListComponent from "../components/slider/SliderList.vue";
import BoardComponent from "../components/Board.vue";
import AboutCourtComponent from "../components/AboutCourt.vue";
import { ContainerType } from "../components/Container.vue";
import TitleComponent from "../components/Title.vue";
import { IRule } from "../types/rule";
import AboutRuleComponent from "../components/About/AboutRule.vue";

@Component({
    components: {
        Container,
        SliderListComponent,
        BoardComponent,
        AboutCourtComponent,
        TitleComponent,
        AboutRuleComponent,
    },
})
export default class AboutView extends Vue {
    containerType = ContainerType;
    courtPhotos = [
        {
            backgroundImgUrl: require("@/assets/summer-court.jpg"),
            routeUrl: "/",
            routeTitle: "Летний корт",
        },
        {
            backgroundImgUrl: require("@/assets/summer-court.jpg"),
            routeUrl: "/",
            routeTitle: "Осенний корт",
        },
        {
            backgroundImgUrl: require("@/assets/summer-court.jpg"),
            routeUrl: "/",
            routeTitle: "Зимний корт",
        },
        {
            backgroundImgUrl: require("@/assets/summer-court.jpg"),
            routeUrl: "/",
            routeTitle: "Весенний корт",
        },
    ];
    courts = [
        {
            image: require("@/assets/7.svg"),
            description: "Летних грунтовых кортов",
        },
        {
            image: require("@/assets/4.svg"),
            description: "Зимних корта с покрытием «искусственная трава»",
        },
        {
            image: require("@/assets/3.svg"),
            description: "Зимних корта с покрытием «hard»",
        },
    ];
    rulesList: IRule[] = [
        {
            title: "Общие положения",
            link: "/about/general",
        },
        {
            title: "Основные определения",
            link: "/about/general-definitions",
        },
        {
            title: "Порядок предоставления игрового времени на кортах",
            link: "/about/schedule",
        },
        {
            title: "Оплата услуг",
            link: "/about/pay",
        },
        {
            title: "Правила поведения на территории и кортах",
            link: "/about/rules-on-place",
        },
        {
            title: "Прочие положения",
            link: "/about/other",
        },
    ];
}
</script>

<style scoped lang="scss">
.about-header {
    background-image: url("../assets/about-bg.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    height: 263px;
    display: flex;
    align-items: center;
    justify-content: center;
    &__title {
        color: #fff;
        font-weight: 700;
        font-size: 48px;
        margin-top: 130px;
    }
}
.about-slide-item {
    border: 1px solid #f7ece1;
    min-width: 100%;
    height: 450px;
    position: relative;
    a {
        position: absolute;
        left: 50px;
        bottom: 40px;
        background-color: #8d86c9;
        padding: 10px 20px;
        font-weight: 600;
        font-size: 18px;
        color: #fff;
        &:hover {
            background-color: #807ab7;
        }
    }
}
.about-board {
    margin: 150px 0;
    .about-title {
        font-weight: 700;
        font-size: 36px;
        margin-bottom: 60px;
    }
    &__details {
        margin-top: 58px;
        display: flex;
        justify-content: space-between;
        gap: 20px;
    }
}
.board-text {
    font-weight: 400;
    font-size: 14px;
}

.about-sidebar {
    width: 366px;
    margin-right: 100px;
    font-weight: 600;
    font-size: 21px;
    color: #333333;
}
.about-views {
    width: 834px;
}
</style>
