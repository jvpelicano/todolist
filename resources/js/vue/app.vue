<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">TodoList</h2>
            <add-item-form 
                 v-on:reloadlist="getList()"
                 />
        </div>
        <listView 
            :items="items"
            v-on:reloadlist="getList()"
            />
    </div>
</template>

<script>
import addItemForm from './addItemForm';
import listView from './listView';

export default {
    components:{
        addItemForm,
        listView
       
    },
    data: function(){
        return{
            items: []
        }
    },
    methods:{
        getList(){
            axios.get('api/items')
            .then( response => {
                this.items = response.data
            })
            .catch(error =>{
                console.log(error);
            })
        }
    },
    created(){
        this.getList();
    }
}
</script>

<style scoped>
    .todoListContainer{
        width: 350px;
        margin: 0 auto;
        color: #2D3748;

    }

    .heading{
        background: #B2F5EA;
        padding: 10px;
        margin-bottom: 10px;
        border-radius: 10px;
        box-shadow: 0 10px 10px -5  px;
    }

    #title{
        text-align:center;
        font-family: 'Nunito', verdana;
    }

</style>

