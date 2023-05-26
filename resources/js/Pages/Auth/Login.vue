<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import JudulNavbar from '@/Components/JudulNavbar.vue';

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
    <div id="sign-in" class="lg:w-[45%] w-[80%] xl:px-[5%] lg:px-[20px] lg:bg-transparent bg-white px-10 py-20 mb-20 rounded-lg">
                <div>
                    <h1 class="font-bold text-xl mb-4 sec-color">Sign in</h1>
                    <p class="md:text-sm md:w-[70%] text-[12px] mb-4">Masuk, dan buat undangan pernikahan kamu, kemudian share undangan kamu.</p>
                    <form @submit.prevent="submit">
                    <div>
                        <TextInput
                        id="email"
                        type="email"
                        placeholder="Alamat Email"
                        class="mt-1 block w-full"
                        v-model="form.email"
                        required
                        autofocus
                        autocomplete="username"
                    />
                    <InputError class="mt-2" :message="form.errors.email" />

                    </div>
                    
                    <div  class="mt-4">    
                    <TextInput
                        id="password"
                        type="password"
                        class="mt-1 block w-full"
                        v-model="form.password"
                        required
                        autocomplete="current-password"
                        placeholder="Password"
                    />

                    <InputError class="mt-2" :message="form.errors.password" />
                    </div>
                    <div class="lg:flex items-center justify-between mt-7 text-center m-auto">
                        <Link
                            :href="route('password.request')"
                            class="font-bold primary-color text-sm lg:block hidden"
                        >
                            Lupa Password ?
                        </Link>

                        <PrimaryButton class="mb-[20px] lg:mb-[0px]" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            SIGN IN
                        </PrimaryButton>

                        <Link
                            :href="route('password.request')"
                            class="font-bold primary-color text-sm lg:hidden block  "
                        >
                            Lupa Password ?
                        </Link>

                        <Link
                            href="#daftar"
                            class="font-bold primary-color text-sm lg:hidden block  "
                        >
                            Belum Punya Akun
                        </Link>
                    </div>
                    </form>
                </div>
            </div>
</template>
