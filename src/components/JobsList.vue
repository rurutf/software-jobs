<template>
    <div class="job-list">
        <transition-group name="list" tag="ul">
            <li
                v-for="job in orderedJobs"
                :key="job.id"
                class="job-list__item">
                <h2 class="job-list__title">{{ job.title }} in {{ job.location }}</h2>
                <div class="job-list__salary">
                    <img
                        src="../assets/diamond-svgrepo-com.svg"
                        title="diamond icon"
                        class="job-list__salary-img">
                    <p class="job-list__salary-item">{{ job.salary }} dollars</p>
                </div>
                <div class="job-list__description">
                    <p>
                        Deeply familiarity with modern JS/CSS/HTML. For example, if I show you some elements styled
                        with flexbox, you shouldn't need to look up what each style does - you should know because
                        you've done it a million times. Map, filter, and enhanced ES6 object literals are your best friends.
                    </p>
                </div>
            </li>
        </transition-group>
    </div>
</template>

<script lang="ts">
import {defineComponent, PropType, computed } from "vue";
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
    setup(props) {
        const orderedJobs = computed(() => {
            return [...props.jobs].sort((a: Job, b: Job) => {
                return a[props.order] > b[props.order] ? 1 : -1;
            })
        })
        return {
            orderedJobs,
        }
    }
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

.list-move {
    transition: all 1s;
}
</style>
