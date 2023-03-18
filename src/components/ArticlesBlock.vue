<template>
    <div class="articles">
        <div class="articles-item">
            <img :src="photo.url" alt="" />
            <div class="articles-item__description">
                <p>{{ photo.title }}</p>
            </div>
            <button class="btn"><a href="#">Подробнее</a></button>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Container from "./Container.vue";
import { IPhoto } from "@/types/index";

@Component({
    components: {
        Container,
    },
    props: {
        photo: {
            type: Object as () => IPhoto,
            default: {},
        },
    },
})
export default class ArticlesBlockComponent extends Vue {
    photo: any;
}
</script>

<style scoped lang="scss">
.articles-item {
    border: 1px solid #f7ece1;
    padding: 30px 40px;
    width: 388px;
    img {
        min-width: 308px;
        height: 240px;
    }
    &__description {
        height: 87px;
        margin-top: 40px;
        margin-bottom: 10px;
        p {
            font-weight: 600;
            font-size: 21px;
        }
    }
    .btn {
        width: 137px;
        height: 45px;
        background-color: #8d86c9;
        border: none;
        font-weight: 600;
        font-size: 18px;
        cursor: pointer;
        a {
            color: #fff;
        }
        &:hover {
            background-color: #807ab7;
        }
    }
}
</style>
