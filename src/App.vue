<template>
    <div class="app">
        <header class="header">
            <div class="header__title">
                <img src="./assets/job-search-svgrepo-com.svg" title="site logo">
                <h1>Software Jobs</h1>
            </div>
            <div class="header__order">
                <button
                    class="header__button"
                    @click="handleClick('title')">
                    order by jobs
                </button>
                <button
                    class="header__button"
                    @click="handleClick('location')">
                    order by location
                </button>
                <button
                    class="header__button"
                    @click="handleClick('salary')">
                    order by salary
                </button>
            </div>
        </header>
        <JobsList
            :jobs="jobs"
            :order="order" />
    </div>
</template>

<script lang="ts">
import JobsList from "@/components/JobsList.vue";

import { defineComponent, ref } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";


export default defineComponent({
    name: 'App',
    components: {
        JobsList,
    },
    setup() {
        const jobs = ref<Job[]>([
            { title: 'Front-end developer', location: 'Moscow', salary: 4000, id: '1' },
            { title: 'Imposer', location: 'Jerusalem', salary: 700, id: '2' },
            { title: 'Ios developer', location: 'Tallinn', salary: 7680, id: '3' },
            { title: 'Front-end', location: 'Shanghai', salary: 98, id: '4' },
            { title: 'Programmer', location: 'Tokyo', salary: 987, id: '5' }
        ])
        const order = ref<OrderTerm>('title')

        const handleClick = (term: OrderTerm) => {
            order.value = term;
        }

        return {
            jobs,
            order,
            handleClick,
        }
    },
})
</script>

<style lang="scss">
.header {
    text-align: center;

    &__order {
        margin-top: 20px;
    }

    &__button {
        margin: 0 10px;
        padding: 8px 16px;
        color: #1195c9;
        border: 3px solid #1195c9;
        background: #d5f0ff;
        border-radius: 4px;
        font-weight: bold;
        cursor: pointer;
    }

    &__title {
        display: flex;
        justify-content: center;

        h1 {
            font-size: 30px;
        }

        img {
            width: 60px;
            margin-right: 20px;
        }
    }
}
</style>
