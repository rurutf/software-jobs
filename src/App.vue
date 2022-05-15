<template>
    <div class="app">
        <JobsList :jobs="jobs" />
    </div>
</template>

<script lang="ts">
import {defineComponent, ref, reactive, toRefs} from "vue";
import Job from "@/types/Job";
import JobsList from "@/components/JobsList.vue";

export default defineComponent({
    name: 'App',
    components: {
        JobsList,
    },
    setup() {
        const jobs = ref<Job[]>([
            { title: 'Frontend', location: 'Moscow', salary: 4000, id: '1' },
            { title: 'Frontend', location: 'Moscow', salary: 4000, id: '2' },
            { title: 'Frontend', location: 'Moscow', salary: 4000, id: '3' },
            { title: 'Frontend', location: 'Moscow', salary: 4000, id: '4' },
            { title: 'Frontend', location: 'Moscow', salary: 4000, id: '5' }
        ])

        return {
            jobs,
        }
    },
})
</script>
