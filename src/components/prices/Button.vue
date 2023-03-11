<template>
    <div>
        <button class="btn">
            {{ buttonContent }}
            <img class="btn__icon" src="@/assets/btn-arrow-icon.svg" alt="" />
        </button>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
    props: {
        buttonContent: String,
    },
})
export default class ButtonComponent extends Vue {
    buttonContent: string | undefined;
}
</script>

<style scoped lang="scss">
.btn {
    width: 526px;
    background-color: #8d86c9;
    border: none;
    padding: 15px 30px;
    color: #ffffff;
    font-weight: 600;
    font-size: 21px;
    margin-bottom: 30px;
    text-align: start;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: space-between;
    transition: 0.3s;
    &:hover {
        padding-right: 60px;
    }
}
</style>
