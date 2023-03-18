<template>
    <div class="rule">
        <router-link :to="rule.link"
            >{{ numberOfRule }}. {{ rule.title }}
        </router-link>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { IRule } from "@/types/rule";

@Component({
    props: {
        rule: Object as () => IRule,
        numberOfRule: Number,
    },
})
export default class AboutRuleComponent extends Vue {}
</script>

<style scoped lang="scss">
.rule {
    margin-bottom: 40px;
    a {
        color: #333333;
        &:focus {
            color: #8d86c9;
        }
    }
}
</style>
