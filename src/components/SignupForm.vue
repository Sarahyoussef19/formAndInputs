<template>
    <form>
        <label>Email</label>
        <input type="email" required v-model="email">

        <label>Password</label>
        <input type="Password" required v-model="password">

        <label>Age: </label>
        <select v-model="age">
            <option value="-18"> - 18 Years Old</option>
            <option value="+18"> + 18 Years Old</option>
        </select>

        <label>skills</label>
        <input type="text" v-model="tempSkill" @keyup="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill">
            <span @click="deleteSkill(skill)">{{ skill }}</span>
        </div>

        <div class="terms">
            <input type="checkbox" required v-model="terms">
            <label>I Accept Terms And Conditions</label>

        </div>
        <div>
            <input type="checkbox" value="newsletter" v-model="preference">
            <label>I Want To Recieve Newsletter</label>
        </div>
        <div>
            <input type="checkbox" value="ofers" v-model="preference">
            <label>I'm Interested In Receiving Offers</label>
        </div>
        <div>
            <input type="checkbox" value="music club" v-model="preference">
            <label>Sign Up for Our Musical Club</label>
        </div>
    </form>

    <p>email: {{ email }}</p>
    <p>password: {{ password }}</p>
    <p>{{ age }}</p>
    <p> terms: {{ terms }}</p>
    <p>preference: {{ preference }}</p>
    <p>{{ skills }}</p>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            age: '',
            terms: false,
            preference: [],
            tempSkill: '',
            skills: []
        }
    },
    methods: {
        addSkill(e) {
            if (e.key === ',' && this.tempSkill) {
                if (!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)
                }

                this.tempSkill = ''
            }
        },
        deleteSkill(skill) {
            this.skills = this.skills.filter((item) => {
                return skill !== item
            })
        }
    }
}
</script>

<style>
form {
    max-width: 450px;
    margin: 30px auto;
    background-color: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}

label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 2px;
    font-weight: bold;
}

input,
select {
    display: block;
    padding: 10px 6px;
    max-width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 2px solid #ddd;
    color: #555;
}

input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 1px;
}

.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background-color: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
</style>