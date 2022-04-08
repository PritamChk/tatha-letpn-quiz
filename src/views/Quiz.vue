<template>
<div class="flex flex-wrap overflow-hidden ">
    <div class ="card" v-for="week in weeks" :key="week">
        <router-link :to="{name : 'Week' , params: {id: week}}">
            <h2 class="text-lg ">week-{{week}}</h2>
        </router-link>
    </div>
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
