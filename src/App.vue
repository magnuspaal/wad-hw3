<template>
    <main id="app">
        <header>
            <strong>Welcome to your dashboard!</strong>
        </header>
        <section id="container">
            <section id="main">
                <div class="content">
                    <Profile class="tab" id="profile-container" v-bind:class="{active: !coursesTabActive}"
                             :name="`${profile.firstname} ${profile.lastname}`"
                             :birthdate="profile.birthdate"
                             :faculty="profile.faculty"
                             :gpa="profile.gpa"/>

                    <Courses class="tab" id="courses-container" :courses="courses" @newCourse="newCourse" v-bind:class="{active: coursesTabActive}"/>
                </div>
                <div class="controls">
                    <button @click="changeTab(false)" id="profile-button" class="pill" v-bind:class="{active: !coursesTabActive}">Profile</button>
                    <button @click="changeTab(true)" id="courses-button" class="pill"  v-bind:class="{active: coursesTabActive}">Courses</button>
                </div>
            </section>
        </section>
        <footer>
            <ul class="links">
                <li>
                    <a href="https://ois2.ut.ee/" target="_blank">OIS</a>
                </li>
                <li>
                    <a href="https://courses.cs.ut.ee/" target="_blank">Courses</a>
                </li>
            </ul>
        </footer>
    </main>
</template>

<script>
    import Profile from "./components/Profile";
    import Courses from "./components/Courses";
    import User from './models/User'
    import Course from './models/Course'

    export default {
        name: 'app',
        methods: {
            changeTab: function (courseSelected) {
                this.coursesTabActive = courseSelected
            },

            getGPA: function () {
                let sum = 0;
                let i = 0;
                this.courses.forEach(function (item, index) {
                    sum += item.grade;
                    i += 1;
                });
                this.profile = new User("John", "Doe", "11/10/1990", "Software Engineering", sum / i)
            },
            newCourse: function (course) {
                this.courses.push(course);
                this.getGPA()
            }
        },
        created: function () {
            console.log(this.profile);
            this.getGPA()
        },
        data: () => {
            return {
                profile: new User("John", "Doe", "11/10/1990", "Software Engineering", 1),
                courses: [
                    new Course("Agile Software Development", 1, 82),
                    new Course("System modeling", 1, 85),
                    new Course("Object Oriented Programming", 2, 99),
                    new Course("Estonian Language Level A2", 2, 65)
                ],
                coursesTabActive: false,
            }
        },
        components: {
            Profile,
            Courses
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    header {
        padding: 20px;
        background-color: #2196F3;
        color: #ffffff;
        text-align: center;
        margin-bottom: 10px;
        height: 60px;
    }

    footer {
        padding: 30px 0;
        background-color: #607D8B;
        margin-top: 10px;
        height: 100px;
        position: absolute;
        bottom: 0;
        width: 100%;
    }

    footer .links {
        display: block;
        width: 100%;
        max-width: 200px;
        margin: 0 auto;
        color: #acd7ff;
        font-size: 11px;
    }

    footer .links a {
        text-decoration: none;
        color: #acd7ff;
    }

    footer .links a:hover {
        text-decoration: underline;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }

    #profile {
        border-bottom: 1px dashed #a7a7a7;
        padding-bottom: 10px;
        margin-bottom: 10px;
        height: 190px;
    }

    #profile div:not(.clear-fix) {
        height: 190px;
        float: left;
        position: relative;
    }

    #profile .avatar {
        width: 35%;
        text-align: center;
    }

    #profile .avatar img {
        width: 180px;
    }

    #profile .info {
        width: 45%;
    }

    #profile #gpa {
        width: 20%;
    }

    #profile #gpa strong {
        position: absolute;
        width: 100%;
        height: 60px;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto auto;
        font-size: 60px;
        line-height: 60px;
        text-align: center;
    }

    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }

    .content .tab {
        display: none;
    }

    .content .tab.active {
        display: block;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }

    .blue-button {
        background-color: #2196F3;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .green-button {
        background-color: #69f378;
        color: #ffffff;
        border: none;
        padding: 10px 10px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
    }

</style>
