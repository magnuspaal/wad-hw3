<template>
    <tr>
        <td>{{id}}</td>
        <td>{{course}}</td>
        <td>{{semester}}</td>
        <td>{{grade}}</td>
    </tr>
</template>

<script>
export default {
    name: "TableRow",
    props:{
        id: Number,
        course: String,
        semester: Number,
        grade: Number
    }
}
</script>

<style>

</style>