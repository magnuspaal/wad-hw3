<template>
    <div id="profile-container" class="tab-active">
        <div id="profile">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <Info :name="name" :birthdate="birthdate" :faculty="faculty"/>
            </div>
            <div id="gpa">
                <strong>{{gpa}}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
import Info from './Info'

export default {
    name: "Profile",
    props: {
        name: String,
        birthdate: String,
        faculty: String,
        gpa: Number
    },
    components: {
        Info
    }
}
</script>

<style>
</style>