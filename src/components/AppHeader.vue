<template>
    <div>
        <img class="title_img" alt="Vue logo" src="../assets/logo.png" />
        <h3 class="title_text">{{title}}</h3>
    </div>
</template>


<script>
    export default {
        name: 'AppHeader',
        props: {
            title: String
        }
    }
</script>

<style>

</style>