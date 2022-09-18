<template>
    <div>
        <Navbar></Navbar>
        <div class="container mt-5">
            <router-link to="/add-employee">Add Employee</router-link>
        </div>
        <router-view />
    </div>
</template>

<script>
import Form from "./Form.vue";
import Navbar from "./Navbar.vue";
import Home from "./Home.vue";
export default {
    data() {
        return {
            data: [],
        };
    },
    methods: {
        async getEmployeeList() {
            await axios
                .get("http://localhost:8080/api/employees")
                .then((res) => {
                    console.log(res);
                })
                .catch((err) => alert(err));
        },
    },
    components: {
        Form,
        Navbar,
        Home,
    },
    mounted() {
        this.getEmployeeList();
        console.log("Component mounted.");
    },
};
</script>
