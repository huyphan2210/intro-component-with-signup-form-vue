<script lang="ts" setup>
import { ref } from 'vue';
import Input from './Input.vue';

const firstName = ref('');
const lastName = ref('');
const email = ref('');
const password = ref('');

const firstNameError = ref('');
const lastNameError = ref('');
const emailError = ref('');
const passwordError = ref('');

const signUp = (event: Event) => {
    event.preventDefault();
    if (isEmpty(firstName.value)) {
        firstNameError.value = "First Name cannot be empty";
    } else {
        firstNameError.value = '';
    }

    if (isEmpty(lastName.value)) {
        lastNameError.value = "Last Name cannot be empty";
    } else {
        lastNameError.value = '';
    }

    if (isEmpty(password.value)) {
        passwordError.value = "Password cannot be empty";
    } else {
        passwordError.value = '';
    }

    if (!isEmail(email.value)) {
        emailError.value = "Looks like this is not an email";
    } else {
        emailError.value = '';
    }
}

const isEmpty = (value: String) => {
    if (!value) return true;

    return false
}

const isEmail = (email: String) => {
    return email
      .toLowerCase()
      .match(
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      );
}
</script>

<template>
    <div class="signUpForm">
        <button id="try" type="button"><span>Try it free 7 days</span> then $20/mo. thereafter</button>
        <form @submit="signUp">
            <Input place-holder="First Name" type="text" @input="(value) => firstName = value" :error-message="firstNameError"></Input>
            <Input place-holder="Last Name " type="text" @input="(value) => lastName = value" :error-message="lastNameError"></Input>
            <Input place-holder="Email Address" type="email" @input="(value) => email = value" :error-message="emailError"></Input>
            <Input place-holder="Password" type="password" @input="(value) => password = value" :error-message="passwordError"></Input>
            <button type="submit">Claim your free trial </button>
            <small>By clicking the button, you are agreeing to our <span>Terms and Services</span> </small>   
        </form>
    </div>
</template>

<style scoped>
    button {
        width: 100%;
        padding: 1rem 2rem;
        border-radius: 0.5rem;
        border-width: 0;
        font-family: Poppins, sans-serif;
        background-color: hsl(154, 59%, 51%);
        box-shadow: 0 0.2rem #31b87c;
        margin-block-end: 1rem;
        color: white;
        text-transform: uppercase;
        letter-spacing: 0.1rem;
    }

        button:hover {
            cursor: pointer;
            background-color: hsla(154, 59%, 51%, 0.75);
        }

    #try {
        text-transform: none;
        background-color: hsl(248, 32%, 49%);
        box-shadow: 0 0.5rem rgba(215,112,112,255);
        letter-spacing: normal;
    }
        #try span{
            font-weight: 600;
        }
        #try:hover{
            opacity: 1;
            background-color: hsla(248, 32%, 49%, 0.9);
        }

    form {
        background-color: white;
        display: grid;
        padding: 2rem;
        border-radius: 0.5rem;
        box-shadow: 0 0.5rem rgba(217,102,102,255);
    }

        small {
            color: hsl(246, 25%, 77%);
            text-align: center;
            font-size: 0.75rem;
        }
            small span {
                color: hsl(0, 100%, 74%) ;
                font-weight: 600;
            }

                small span:hover {
                    cursor: pointer;
                }

@media screen and (max-aspect-ratio: 1 / 1) {
    .signUpForm {
        padding: 2rem;
    }

        form {
            padding: 1rem;
        }
}
</style>