<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import JudulNavbar from '@/Components/JudulNavbar.vue';
import Login from '@/Pages/Auth/Login.vue';
import Register from '@/Pages/Auth/Register.vue';



import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <div>
        <Head title="Log in" />

        <JudulNavbar></JudulNavbar>


        <div class="flex mt-[20vh]  w-[100%] flex-wrap justify-center lg:justify-evenly  items-start ">
            
            <Login></Login>

            <div class="hidden lg:block bg-[#CDCDCD] w-[2px] h-[500px]"></div>
            
            <Register></Register>
        </div>
    </div>

    <br><br><br><br><br><br>

</template>
