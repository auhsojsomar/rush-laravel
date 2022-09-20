<template>
    <div>
        <form action="">
            <div class="row">
                <div class="col-md-6">
                    <label for="first_name" class="form-label"
                        >First Name</label
                    >
                    <input
                        type="text"
                        class="form-control"
                        id="first_name"
                        v-model="first_name"
                    />
                </div>
                <div class="col-md-6">
                    <label for="last_name" class="form-label">Last Name</label>
                    <input
                        type="text"
                        class="form-control"
                        id="last_name"
                        v-model="last_name"
                    />
                </div>
                <div class="col-md-6">
                    <label for="address" class="form-label">Address</label>
                    <input
                        type="text"
                        class="form-control"
                        id="address"
                        v-model="address"
                    />
                </div>
                <div class="col-md-6">
                    <label for="postal_code" class="form-label"
                        >Postal Code</label
                    >
                    <input
                        type="text"
                        class="form-control"
                        id="postal_code"
                        v-model="postal_code"
                    />
                </div>
                <div class="col-md-6">
                    <label for="contact_number" class="form-label"
                        >Contact Number</label
                    >
                    <input
                        type="text"
                        class="form-control"
                        id="contact_number"
                        v-model="contact_number"
                    />
                </div>
                <div class="col-md-6">
                    <label for="email" class="form-label">Email</label>
                    <input
                        type="text"
                        class="form-control"
                        id="email"
                        v-model="email"
                    />
                </div>
                <div class="col-md-6">
                    <label for="username" class="form-label">Username</label>
                    <input
                        type="text"
                        class="form-control"
                        id="username"
                        v-model="username"
                    />
                </div>
                <div class="col-md-6">
                    <label for="password" class="form-label">Password</label>
                    <input
                        type="password"
                        class="form-control"
                        id="password"
                        v-model="password"
                    />
                </div>
                <div class="col-md-12">
                    <button class="btn btn-primary" @click="storeEmployee">
                        Add Employee
                    </button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "Form",
    data() {
        return {
            first_name: "",
            last_name: "",
            address: "",
            postal_code: "",
            contact_number: "",
            email: "",
            username: "",
            password: "",
        };
    },
    methods: {
        async storeEmployee() {
            const employee = await axios
                .post("http://localhost:8080/api/employees", {
                    first_name: this.first_name,
                    last_name: this.last_name,
                    address: this.address,
                    postal_code: this.postal_code,
                    contact_number: this.contact_number,
                    email: this.email,
                    username: this.username,
                    password: this.password,
                })
                .then((res) => {
                    alert("Employee Added");
                })
                .catch((err) => {
                    alert(err.message);
                });
        },
    },
};
</script>

<style lang="scss" scoped></style>
