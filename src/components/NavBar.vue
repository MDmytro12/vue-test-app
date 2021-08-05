<template>
    <div>
        <h1>
            Navigation on the site : 
        </h1>
        <ul>
            <li>
                <router-link to="/">Move to home page!</router-link>
            </li>
            <li>
                <router-link to='/todos'>Move to todos page!</router-link>
            </li>
        </ul>
    </div>
</template>

<style>
    ul{
        display:flex;
        flex-direction: column;
        
        padding: 15px 10px;

        border: 3px solid blue;
    }
</style>