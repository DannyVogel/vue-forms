<template>
    <form @submit.prevent="handleSubmit">
        <label>Email:</label>
        <input type="email" name="email" placeholder="Enter your email address" v-model="email"/>

        <label>Password:</label>
        <input type="password" name="password" placeholder="Enter your password" v-model="password"/>
        <p v-if="passwordError" class="error">{{passwordError}}</p>

        <label>Role:</label>
        <select v-model="role">
            <option value="Developer">Developer</option>
            <option value="Designer">Designer</option>
        </select>

        <div class="terms">
            <input type="checkbox" v-model="terms" required/>
            <label>Accept Terms and Conditions</label>
        </div>

        <div>
            <input type="checkbox" value='Mario' v-model="names"/>
            <label>Mario</label>
        </div>
        <div>
            <input type="checkbox" value='Luigi' v-model="names"/>
            <label>Luigi</label>
        </div>
        <div>
            <input type="checkbox" value='Yoshi' v-model="names"/>
            <label>Yoshi</label>
        </div>

        <label>Skills</label>
        <input type="text" v-model="tempSkill" @keyup="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill">
            <span @click="deleteSkill(skill)">{{skill}}</span>
        </div>

        <div class="submit">
            <button type="submit">Create an Account</button>
        </div>

    </form>
    <p>Email: {{email}}</p>
    <p>Password: {{password}}</p>
    <p>Role: {{role}}</p>
    <p>Terms: {{terms ? 'Accepted' : 'Not accepted'}}</p>
    <p>Names: {{names.join(', ')}}</p>
    <p>Skills: {{skills.join(', ')}}</p>
</template>

<script>
export default {
    name: 'SignUpForm',
    components: {

    },
    data() {
        return {
            email: '',
            password: '',
            role: 'Designer',
            terms: false,
            names: [],
            tempSkill: '',
            skills: [],
            passwordError: ''
        }
    },
    methods: {
        addSkill(e) {
            if (e.key === ',' && this.tempSkill) {
                if (!this.skills.includes(this.tempSkill)){
                    this.skills.push(this.tempSkill.slice(0, -1));
                }
                this.tempSkill = '';
            }
        },
        deleteSkill(skill) {
            this.skills = this.skills.filter(s => s !== skill);
        },
        handleSubmit() {
            // validation
            this.passwordError = this.password.length < 6 ? 'Password must be at least 6 characters' : '';
            if (!this.passwordError) {
                // submit form
                console.log({
                    email: this.email,
                    password: this.password,
                    role: this.role,
                    terms: this.terms,
                    names: this.names,
                    skills: this.skills
                });
            }
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
        text-align: left;
    }
    label {
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        color: #aaa;
        text-transform: uppercase;
        letter-spacing: 2px;
        font-weight: bold;
    }
    input, select {
        display: block;
        box-sizing: border-box;
        width: 100%;
        padding: 10px 6px;
        color: #555;
        border: none;
        border-bottom: 1px solid #ddd;
    }
    input[type="checkbox"] {
        display: inline-block;
        width: 16px;
        margin-right: 0 10px 0 0;
        position: relative;
        top: 2px;
    }
    .pill {
        display: inline-block;
        margin: 20px 10px 0 0;
        padding: 6px 12px;
        background: #eee;
        border-radius: 20px;
        font-size: 0.8em;
        color: #777;
        letter-spacing: 1px;
        font-weight: bold;
        cursor: pointer;
    }
    button {
        background: #0b6dff;
        border: none;
        padding: 10px 20px;
        margin-top: 20px;
        color: #fff;
        border-radius: 20px;
    }
    .submit {
        text-align: center;
    }  
    .error {
        color: red;
        font-size: 0.8em;
        margin-top: 5px;
        font-weight: bold;
    }
</style>