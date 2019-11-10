<template>
    <ul>
        <li id="name">{{name}}</li>
        <li id="birthdate">{{birthdate}}</li>
        <li id="faculty">{{faculty}}</li>
    </ul>

</template>

<script>
    export default {
        name: "Info",
        props: {
            name: String,
            birthdate: String,
            faculty: String
        }
    }
</script>

<style>
</style>