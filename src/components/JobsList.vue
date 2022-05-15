<template>
    <div class="job-list">
        <p>Ordered by {{ order }}</p>
        <ul>
            <li
                v-for="job in jobs"
                :key="job.id"
            class="job-list__item">
                <h2 class="job-list__title">{{ job.title }} in {{ job.location }}</h2>
                <div class="job-list__salary">
                    <p class="job-list__salary-item">{{ job.salary }} dollars</p>
                </div>
                <div class="job-list__description">
                    <p>lorem ipsum</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import {defineComponent, PropType} from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
    props: {
        jobs: {
            type: Array as PropType<Job[]>,
            required: true,
        },
        order: {
            type: String as PropType<OrderTerm>,
            required: true,
        }
    },
})
</script>

<style lang="scss">
.job-list {
    max-width: 960px;
    margin: 40px auto;

    ul {
        padding: 0;
    }

    &__item {
        margin: 16px 0;
        padding: 16px;
        background: #ffffff;
        border-radius: 10px;
        list-style-type: none;
    }

    &__title {
        margin: 0 0 10px;
        text-transform: capitalize;
    }

    &__salary {
        display: flex;
    }

    &__salary-img {
        width: 30px;
    }

    &__salary-item {
        margin: 10px 8px;
        color: #17bf66;
        font-weight: bold;
    }
}
</style>
