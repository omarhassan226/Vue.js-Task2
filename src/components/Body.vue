<template>
    <div>
        <table v-if="!isModalOpened" class="table-striped w-100 h-100 table-bordered">
            <thead>
                <tr>
                    <th>id</th>
                    <th>name</th>
                    <th>city</th>
                    <th>delete</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="std in students" :key="std.id">
                    <td>{{ std.id }}</td>
                    <td>{{ std.name }} </td>
                    <td>{{ std.city }}</td>
                    <td><button class="delete-button" v-on:click="deleteStudent(std.id)">delete</button></td>
                </tr>
            </tbody>
            <tfoot>
                <tr>
                    <th colspan="4" class="col-6 text-center">
                        #N.O Students = {{ students.length }}
                    </th>
                </tr>
            </tfoot>
        </table>

        <form @submit="addStudent" v-if="isModalOpened">
            <div class="mb-3">
                <label for="exampleInputname" class="form-label"> name</label>
                <input type="" class="form-control" id="exampleInputname" aria-describedby="emailHelp">
                <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
            </div>
            <div class="mb-3">
                <label for="exampleInputcity1" class="form-label">city</label>
                <input type="city" class="form-control" id="exampleInputcity1">
            </div>

            <button type="submit" class="submit-button">Submit</button>

            <button type="button" v-on:click="toggleModal" class="cancel-button">Cancel</button>
        </form>

        <button v-else-if="!isModalOpened" v-on:click="toggleModal" class="add-button">Add</button>

    </div>
</template>

<script>
import students from "../students";
export default {
    data() {

        return {
            students: students,
            isModalOpened: false
        };
    },
    methods: {
        addStudent(e) {
            let num = students[students.length - 1].id + 1
            students.push({ id: num, name: e.target[0].value, city: e.target[1].value })
            this.isModalOpened = false
            e.target[0].value = e.target[1].value = ''
        },


        deleteStudent(id) {
            let index = this.students.findIndex((std) => std.id === id);
            this.students.splice(index, 1)
        },

        toggleModal() {
        this.isModalOpened = !this.isModalOpened;
        }
    }
}
</script>

<style>
body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
}

table {
    margin-top: 20px;
}

table th {
    background-color: #333;
    color: #fff;
    text-align: center
}

table td {
    padding: 10px;
    text-align: center;
}

form {
    margin-top: 20px;
}

.form-control {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}


.delete-button {
    padding: 10px 20px;
    background-color: #cf3238;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
}

.submit-button,
.add-button{
    padding: 10px 20px;
    background-color: #07c87b;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
    margin-bottom: 10px;
}

.submit-button:hover,
.add-button:hover,
.cancel-button:hover{
    background-color: #37d193;
}

.cancel-button{
    margin-left: 10px;
    padding: 10px 20px;
    background-color: #07c87b;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
    margin-bottom: 10px;
}

.delete-button:hover{
    background-color: #e65358;
}
</style>
