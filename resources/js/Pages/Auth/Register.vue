<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name_laki: '',
    name_perempuan: '',
    telp: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
            <div id="daftar" class="lg:w-[45%] w-[80%] xl:px-[5%] lg:px-[20px] lg:bg-transparent bg-white px-10 py-20 mb-20 rounded-lg">



                <div >
                    <h1 class="lg:flex justify-end font-bold text-xl mb-4 sec-color"  >DAFTAR</h1>
                    <p class="lg:flex  justify-end text-sm ">Buat Pernikahan Digital Kamu dengan elegan,</p>
                    <p class="lg:flex  justify-end text-sm  mb-4 font-bold">Your alternative wedding invitation</p>

                    <form @submit.prevent="submit">
                    <div>

                            <TextInput
                                id="email"
                                type="email"
                                class="mt-1 block w-full"
                                v-model="form.email"
                                required
                                placeholder="Alamat Email"
                                autocomplete="username"
                            />

                            <InputError class="mt-2" :message="form.errors.email" />
                        </div>
                        <div  class="mt-4">

                            <TextInput
                                id="telp"
                                type="text"
                                class="mt-1 block w-full"
                                v-model="form.telp"
                                required
                                autofocus
                                placeholder="Nomor HP"
                                autocomplete="name"
                            />

                            <InputError class="mt-2" :message="form.errors.telp" />
                        </div>

                        <div  class="mt-4">

                            <TextInput
                                id="name_laki"
                                type="text"
                                class="mt-1 block w-full"
                                v-model="form.name_laki"
                                required
                                autofocus
                                placeholder="Nama Panggilan Laki-Laki"
                                autocomplete="name"
                            />

                            <InputError class="mt-2" :message="form.errors.name_laki" />
                        </div>

                        <div  class="mt-4">

                            <TextInput
                                id="name_perempuan"
                                type="text"
                                class="mt-1 block w-full"
                                v-model="form.name_perempuan"
                                required
                                autofocus
                                placeholder="Nama Panggilan Perempuan"
                                autocomplete="name"
                            />

                            <InputError class="mt-2" :message="form.errors.name_perempuan" />
                        </div>

                        

                        <div class="mt-4">

                            <TextInput
                                id="password"
                                type="password"
                                class="mt-1 block w-full"
                                v-model="form.password"
                                required
                                autocomplete="new-password"
                                placeholder="Password"
                            />

                            <InputError class="mt-2" :message="form.errors.password" />
                        </div>

                        <div class="mt-4">

                            <TextInput
                                id="password_confirmation"
                                type="password"
                                class="mt-1 block w-full"
                                v-model="form.password_confirmation"
                                required
                                autocomplete="new-password"
                                placeholder="Konfirmasi Password"

                            />

                            <InputError class="mt-2" :message="form.errors.password_confirmation" />
                        </div>

                        <div class="flex items-center justify-end mt-4">
                            <!-- <Link
                                :href="route('login')"
                                class="underline text-sm text-gray-600 hover:text-gray-900 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                            >
                                Already registered?
                            </Link> -->

                            <PrimaryButton class="px-[20px] w-full flex items-center justify-between" :class="{ 'opacity-25': form.processing }" :disabled="form.processing" >
                                BUAT UNDANGANMU SEKARANG  <img :src="'storage/Union.png'" alt="">
                            </PrimaryButton>
                        </div>
                    </form>
                </div>
            </div>
</template>
