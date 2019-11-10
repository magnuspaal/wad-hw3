<template>
    <div id="profile-container" class="tab-active">
        <div id="profile">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{name}}</li>
                    <li id="birthdate">{{birthdate}}</li>
                    <li id="faculty">{{faculty}}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{gpa}}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
import Courses from './Courses'

export default {
    name: "Profile",
    props: {
        name: String,
        birthdate: String,
        faculty: String,
        gpa: Number
    }
}
</script>

<style>
</style>