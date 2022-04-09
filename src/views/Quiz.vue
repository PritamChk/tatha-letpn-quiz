<template class="bg-black">
<div class="flex flex-wrap overflow-hidden">
    <template v-for="week in weeks" :key="week">
        <router-link :to="{name : 'Week' , params: {id: week}}">
            <h2 
            class="card text-lg font-medium text-center text-white "
            >week-{{week}}</h2>
        </router-link>
    </template>
</div>
</template>

<script>
import Week from './Week.vue'
export default {
    name: 'Quiz',
    components:{
        Week,
    },
    data(){
        return{
            weeks : 12
        }
    }

}
</script>
