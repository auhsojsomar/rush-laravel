<template>
    <div>
        <table class="table table-striped">
            <thead>
                <tr>
                    <th>Firstname</th>
                    <th>Lastname</th>
                    <th>Address</th>
                    <th>Postal Code</th>
                    <th>Contact Number</th>
                    <th>Email</th>
                    <th>Username</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody v-for="employee in employees" :key="employee.id">
                <td>{{ employee.first_name }}</td>
                <td>{{ employee.last_name }}</td>
                <td>{{ employee.address }}</td>
                <td>{{ employee.postal_code }}</td>
                <td>{{ employee.contact_number }}</td>
                <td>{{ employee.email }}</td>
                <td>{{ employee.username }}</td>
                <td>
                    <button
                        type="button"
                        class="btn bg-primary text-white mx-1"
                    >
                        Edit
                    </button>
                    <button
                        type="button"
                        class="btn bg-danger text-white mx-1"
                        @click="deleteEmployee(employee.id)"
                    >
                        Delete
                    </button>
                </td>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "Home",
    data() {
        return {
            employees: [],
        };
    },
    methods: {
        async getEmployeeList() {
            let employee;
            await axios
                .get("http://localhost:8080/api/employees")
                .then((res) => {
                    this.employees = res.data;
                })
                .catch((err) => alert(err));
        },
        async deleteEmployee(id) {
            let x = window.confirm("You want to delete the employee?");

            if (x) {
                await axios
                    .delete(`http://localhost:8080/api/employees/${id}`)
                    .then((res) => {
                        alert("Employee Deleted");
                        location.reload();
                        // reload for now my i have a problem with vue-router
                    })
                    .catch((err) => alert(err.message));
            }
        },
    },
    mounted() {
        this.getEmployeeList();
    },
};
</script>

<style lang="scss" scoped></style>
