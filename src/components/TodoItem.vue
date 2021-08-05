<template>
    <div>
        <li> 
            <input type="checkbox" v-on:change="todo.completed = !todo.completed"> 

            <strong class="index">
                {{index + 1}}
            </strong>

            <strong v-bind:class="{done : todo.completed}">
            {{todo.title|toUppercase}}
            </strong>

            <button class='rm' v-on:click="$emit('remove-todo' , todo.id)">&times;</button>
        </li>
    </div>
</template>

<script>
export default {
    props:{
        todo : {
            type: Object ,  
            required: true
        },
        index: {
            type: Number
        }
    },
    filters:{
            toUppercase(value){
                console.log(value)
                return value.toUpperCase()
            }
        }
}
</script>

<style>
    li{
        list-style:none;

        padding: 5px;

        border: 1px solid blue;

        display: flex;
        justify-content: space-between;

        margin-bottom: 10px;

        letter-spacing: .4em;
    }
    li:hover{
        background-color: blue;
        color: white;
    }
    .rm{
        background-color: red;
        color: white;
        border: none;
        border-radius: 100px;
    }
    .done{
        font-weight: 600;
        text-decoration: underline;
        color: red;
    }
    .index{
        background-color: black;
        color: white;
        padding: 3px;
        padding-left: 8px;
        text-align: center;
    }
</style>