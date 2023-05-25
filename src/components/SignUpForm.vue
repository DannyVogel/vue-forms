<template>
    <form>
        <label>Email:</label>
        <input type="email" name="email" placeholder="Enter your email address" v-model="email"/>
        <label>Password:</label>
        <input type="password" name="password" placeholder="Enter your password" v-model="password"/>
    </form>
    <p>Email: {{email}}</p>
    <p>Password: {{password}}</p>
</template>

<script>
export default {
    name: 'SignUpForm',
    components: {

    },
    data() {
        return {
            email: '',
            password: ''
        }
    }

}

</script>

<style>
    form {
        max-width: 420px;
        margin: 30px auto;
        padding: 40px;
        background: #fff;
        border-radius: 10px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    label {
        display: inline-block;
        margin-bottom: 25px 0 15px;
        font-size: 0.6em;
        color: #aaa;
        text-transform: uppercase;
        letter-spacing: 2px;
        font-weight: bold;
        text-align: left;
    }
    input {
        display: block;
        box-sizing: border-box;
        width: 100%;
        padding: 10px 6px;
        color: #555;
        border: none;
        border-bottom: 1px solid #ddd;
    }
</style>