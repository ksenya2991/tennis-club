<template>
    <div>
        <header class="news-header">
            <h2 class="news-header__title">Новости</h2>
        </header>
        <section class="articles">
            <Container :style-type="containerType.GRID_NEWS">
                <ArticlesBlockComponent
                    v-for="(photo, index) in photos"
                    :key="index"
                    :photo="photo"
                />
            </Container>
        </section>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Container from "@/components/Container.vue";
import { getPhotos } from "@/api/api";
import { IPhoto } from "@/types/index";
import ArticlesBlockComponent from "@/components/ArticlesBlock.vue";
import { ContainerType } from "@/components/Container.vue";

@Component({
    components: {
        Container,
        ArticlesBlockComponent,
    },
})
export default class NewsView extends Vue {
    containerType = ContainerType;
    photos: IPhoto[] = [];
    async mounted() {
        try {
            const response = await getPhotos();
            const data = response.data;

            if (data.length) {
                this.photos = data;
            }
        } catch (error) {
            console.log(error);
        }
    }
}
</script>

<style scoped lang="scss">
.news-header {
    background-image: url("../assets/news-bg.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    height: 263px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 80px;
    &__title {
        color: #fff;
        font-weight: 700;
        font-size: 48px;
        margin-top: 130px;
    }
}
</style>
