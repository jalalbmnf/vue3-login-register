<template>
    <main class="login">
        <section class="forms">
            <form class="register" @submit.prevent="register">
                <h2>Register</h2>
                <input type="email" placeholder="Email" v-model="registerForm.email" />
                <input type="password" placeholder="Password" v-model="registerForm.password" />
                <input type="submit" value="Register" />
            </form>
            <form class="login" @submit.prevent="login">
                <h2>Login</h2>
                <input type="email" placeholder="Email" v-model="loginForm.email" />
                <input type="password" placeholder="Password" v-model="loginForm.password" />
                <input type="submit" value="Login" />
            </form>
        </section>
    </main>
</template>

<script>

import { ref } from "vue"
import { useStore } from "vuex"

export default {
    setup() {
        const loginForm = ref({});
        const registerForm = ref({});
        const store = useStore()

        const login = () => {
            store.dispatch("login", loginForm.value)
        }

        const register = () => {
            store.dispatch("register", registerForm.value)
        }


        return {
            loginForm,
            registerForm,
            login,
            register
        }
    },
}
</script>

<style>
.forms {
    display: flex;
    min-height: 100vh;
}
form {
    flex: 1 1 0%;
    padding: 8rem 1rem 1rem;
}
form.register {
    color: #fff;
    background-color: rgb(245, 66, 101);
    background-image: linear-gradient(
        to bottom right,
        rgb(245, 66, 101) 0%,
        rgb(189, 28, 60) 100%
    );
}
h2 {
    font-size: 2rem;
    text-transform: uppercase;
    margin-bottom: 2rem;
}
input {
    appearance: none;
    border: none;
    outline: none;
    background: none;
    display: block;
    width: 100%;
    max-width: 400px;
    margin: 0 auto;
    font-size: 1.5rem;
    margin-bottom: 2rem;
    padding: 0.5rem 0rem;
}
input:not([type="submit"]) {
    opacity: 0.8;
    transition: 0.4s;
}
input:focus:not([type="submit"]) {
    opacity: 1;
}
input::placeholder {
    color: inherit;
}
form.register input:not([type="submit"]) {
    color: #fff;
    border-bottom: 2px solid #fff;
}
form.login input:not([type="submit"]) {
    color: #2c3e50;
    border-bottom: 2px solid #2c3e50;
}
form.login input[type="submit"] {
    background-color: rgb(245, 66, 101);
    color: #fff;
    font-weight: 700;
    padding: 1rem 2rem;
    border-radius: 0.5rem;
    cursor: pointer;
    text-transform: uppercase;
}
form.register input[type="submit"] {
    background-color: #fff;
    color: rgb(245, 66, 101);
    font-weight: 700;
    padding: 1rem 2rem;
    border-radius: 0.5rem;
    cursor: pointer;
    text-transform: uppercase;
}
</style>