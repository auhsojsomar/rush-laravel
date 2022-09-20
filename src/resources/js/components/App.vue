<template>
    <div>
        <Navbar></Navbar>
        <div class="container mt-5">
            <!-- <router-link to="/add-employee">Add Employee</router-link> -->
            <Home></Home>
            <Form></Form>
        </div>
        <!-- <router-view /> -->
    </div>
</template>

<script>
import Form from "./Form.vue";
import Navbar from "./Navbar.vue";
import Home from "./Home.vue";
export default {
    components: {
        Form,
        Navbar,
        Home,
    },
    mounted() {
        console.log("Component mounted.");
    },
};
</script>
