<template>
    <div>
        
        <div v-for="(item, index) in items" :key="index">
            
            <list-item
                :item="item"
                class="item"
                v-on:itemchanged="$emit('reloadlist')"
             />
        </div>
    </div>
</template>

<script>
import listItem from './listItem.vue'
export default {
    props: ['items'],
    components:{
        listItem,
    }
    
}
</script>

<style>
    .item{
        background: #B2F5EA;
        padding: 5px;
        margin-top: 5px;
        font-family: nunito;
        border-radius: 4px;
        box-shadow: 0 10px 10px -5px;
    }

</style>