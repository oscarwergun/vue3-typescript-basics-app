<template>
    <div class="job-list">
        <p>Order by {{ order }}</p>
        <!-- Vue animation with transition-group -->
        <transition-group name="list" tag="ul">
            <li v-for="job in orderedJobs" :key="job.id">
                <h3>{{ job.title }} in {{ job.location }}</h3>
                <div class="salary">
                    <p>{{ job.salary }} SEK</p>
                </div>
                <p class="desc">Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem deserunt doloribus ipsa ipsam
                    quas odio eligendi ratione possimus?</p>
            </li>
        </transition-group>
    </div>
</template>

<script lang="ts">
import { PropType, defineComponent, computed } from 'vue'
import Job from '@/types/Job';
import OrderTerm from '@/types/OrderTerm';
export default defineComponent({
    name: "JobList",
    props: {
        jobs: {
            required: true,
            type: Array as PropType<Job[]>
        },
        order: {
            required: true,
            type: String as PropType<OrderTerm>
        }
    },
    setup(props) {
        const orderedJobs = computed(() => {
            // sort function is destructive so we want to spread and get all existing before we are sorting out the list 
            return [...props.jobs].sort((a: Job, b: Job) => {
                return a[props.order] > b[props.order] ? 1 : -1
            })
        })
        return { orderedJobs }
    }
})
</script>

<style scoped>
.job-list {
    max-width: 960px;
    margin: 40px auto;
}

ul {
    list-style: none;
    padding: 0;
}

li {
    list-style-type: none;
    background: var(--list-bg);
    border-radius: 10px;


}

.job-list h3 {
    text-transform: uppercase;
    text-align: center;
    padding-top: 10px;
}

.salary {
    font-size: 18px;
    text-align: center;
    color: var(--salary);
    font-weight: 600;
}

.desc {
    margin: 10px;
    padding: 5px;
}

.list-move {
    transition: all 1s;
}
</style>