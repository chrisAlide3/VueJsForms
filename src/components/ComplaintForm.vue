<template>
    <div class="row">
        <div class="col-8 mx-auto mt-4">
            <h1>File  a complaint</h1>
            <hr>
        <form>
            <div class="form-group"> 
                <label for="email">Email</label>
                <input 
                        type="email" 
                        class="form-control" 
                        id="email" 
                        aria-describedby="emailHelp" 
                        placeholder="Enter email"
                        v-model.trim="userData.email"
                >
                        <!-- Modifier .trim will remove leading and ending blanks -->
                <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
            </div>

            <div class="form-group">
                <label for="password">Password</label>
                <input 
                        type="password" 
                        class="form-control" 
                        id="password" 
                        placeholder="Password"
                        v-model.lazy="userData.password"
                >
                        <!-- The .lazy modifier on v-model only updates the value once we exit the field -->
            </div>

            <div class="form-group">
                <label for="age">Age</label>
                <input 
                        type="text" 
                        class="form-control" 
                        id="age" 
                        aria-describedby="ageHelp" 
                        placeholder="Enter your age"
                        v-model.number="userData.age"
                >
                        <!-- Modifier .number will convert the value to a number -->
            </div>

            <div class="form-group">
                <label for="message">Message</label>
                <textarea 
                            class="form-control" 
                            id="message" 
                            rows="6"
                            v-model="message">
                </textarea>
            </div>

            <div class="form-check form-check-inline">
                <input 
                        class="form-check-input" 
                        type="checkbox" 
                        id="sendMail" 
                        value="sendMail"
                        v-model="sendMail"
                >
                <label class="form-check-label" for="sendMail">Send Mail</label>
            </div>
            <div class="form-check form-check-inline">
                <input 
                        class="form-check-input" 
                        type="checkbox" 
                        id="sendInfoMail" 
                        value="sendInfoMail"
                        v-model="sendMail"
                >
                <label class="form-check-label" for="sendInfoMail">Send Infomail</label>
            </div>

            <div class="form-row mt-2 mb-3">
                <div class="col-8">
                    <div class="form-check form-check-inline">
                        <input 
                                class="form-check-input" 
                                type="radio" 
                                name="gender" 
                                id="male" 
                                value="Male"
                                v-model="gender"
                        >
                        <label class="form-check-label" for="inlineRadio1">Male</label>
                    </div>
                    <div class="form-check form-check-inline">
                        <input 
                                class="form-check-input" 
                                type="radio" 
                                name="gender" 
                                id="female" 
                                value="Female"
                                v-model="gender"
                        >
                        <label class="form-check-label" for="inlineRadio2">Female</label>
                    </div>
                </div>
            </div>

            <label for="priority">Priority</label>
            <select 
                    id="priority"
                    class="custom-select mb-3"
                    v-model="priority">
                <option v-for="element in priorities" :key=element
                        :value=element>

                            {{ element }}
                </option>
            </select>
            <app-switch v-model="dataSwitch"></app-switch>
            <hr>

            <button 
                    type="submit" 
                    class="btn btn-primary mt-3"
                    @click.prevent="submitForm">
                Submit
            </button>

            <hr>
        </form>

        <!-- Display user data -->    

        <div v-if="isSubmited" class="card">
            <div class="card-body">
                <h5 class="card-title">Your Data:</h5>
                <p class="card-text">Email address: {{userData.email}}</p>
                <p class="card-text">Password: {{userData.password}}</p>
                <p class="card-text">Age: {{userData.age}}</p>
                <p style="white-space: pre" class="card-text">Message: {{message}}</p>
                <p class="card-text"><strong>Send Mail?</strong></p>
                <ul>
                    <li v-for="mail in sendMail" :key=mail>{{ mail }}</li>
                </ul>
                <p class="card-text">Gender: {{ gender }}</p>
                <p class="card-text">Priority: {{ priority }}</p>
                <p class="card-text">Switched: {{ dataSwitch }}</p>
            </div>
        </div>
        </div>
    </div>
</template>

<script>
import Switch from "./Switch"

    export default {
        data() {
            return {
                userData: {
                    email: '',
                    password: '',
                    age: 50,
                },
                message: "This is a test message",
                sendMail: [],
                gender: "Male",
                priorities: ["high", "medium", "low"],
                priority: "medium",
                dataSwitch: true,
                isSubmited: false,
        }
    },
    methods: {
        submitForm() {
            this.isSubmited = true;
        }
    },

    components: {
        "appSwitch": Switch
    }
}
</script>

<style scoped>
    label {
        font-weight: bold
    }
    .card-title {
        background-color: lightgray;
        height: 50px;
        padding: 15px 0px 15px 5px
    }
</style>    <div>

    </div>

