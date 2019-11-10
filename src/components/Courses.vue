<template>
    <div id="courses-container" class="tab-active">
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
            </thead>
            <tbody>
            <TableRow v-for="(row, i) in courses"
                      :id="i"
                      :course="row.title"
                      :semester="row.semester"
                      :grade="row.grade"
                      :key="i">
            </TableRow>
            </tbody>
        </table>
        <br>
        <br>
        <div>
            <button id="add-course-button" @click="changeAddCourse(!changeAdd)" class="blue-button">+</button>
            <span id="add-course" v-if="changeAdd == false">
                <input class="input" type="text" id="title" placeholder="Title" v-model="title"/>
                <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester" v-model="semester"/>
                <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade" v-model="grade"/>
                <button class="green-button" id="save-course" @click="addCourse">Save</button>
                <button class="grey-button" id="cancel-course" @click="changeAddCourse(!changeAdd), clear()">Cancel</button>
            </span>
        </div>
    </div>
</template>

<script>
import TableRow from "./TableRow"
import Course from '../models/Course'
import Profile from './Profile'

export default {
    name: "Courses",
    components: {TableRow},
    props: {
        courses: Array
    },
    data: () => {
        return {
            title: "",
            semester: "",
            grade: "",
            changeAdd: true
        }
    },
    methods: {
        addCourse: function () {
            let course = new Course(this.title, parseInt(this.semester), parseInt(this.grade));
            this.$emit("newCourse", course);
        },
        changeAddCourse: function (state) {
            this.changeAdd = state
        },
        clear: function () {
            this.semester = ''
            this.title = ''
            this.grade = ''
        },
    }
}
</script>

<style>
    #add-course {
        display: block;
    }
</style>