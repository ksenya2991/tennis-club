<template>
    <div>
        <div class="menu" :style="{ color: textColor }">
            <ul class="menu__list">
                <router-link tag="li" to="/">Главная</router-link>
                <router-link tag="li" to="/about">О клубе</router-link>
                <router-link tag="li" to="/news">Новости</router-link>
                <router-link tag="li" to="/services">Услуги</router-link>
                <router-link tag="li" to="/tennis">Детский теннис</router-link>
                <router-link tag="li" to="/gallery">Галерея</router-link>
                <router-link tag="li" to="/prices">Цены</router-link>
                <router-link tag="li" to="/contacts">Контакты</router-link>
            </ul>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
    props: {
        textColor: {
            type: String,
            required: false,
            default: "#fff",
        },
    },
})
export default class MenuComponent extends Vue {
    textColor: string | undefined;
}
</script>

<style scoped lang="scss">
.menu {
    &__list {
        display: flex;
        gap: 20px;
        cursor: pointer;
    }
    li {
        position: relative;
        display: block;
        &::before {
            content: "";
            left: 0;
            width: 0;
            height: 2px;
            position: absolute;
            bottom: -3px;
            transition: width 0.5s;
            background-color: #fff;
            border-radius: 5px;
        }
        &:hover::before {
            width: 100%;
        }
    }
}
</style>
