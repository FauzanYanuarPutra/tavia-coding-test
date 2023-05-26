<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import JudulNavbar from '@/Components/JudulNavbar.vue';
import { Link, useForm, usePage } from '@inertiajs/vue3';
import TextInput from '@/Components/TextInput.vue';
import InputLabel from '@/Components/InputLabel.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';




defineProps({
    mustVerifyEmail: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const user = usePage().props.auth.user;

const form = useForm({
    name_laki: user.name_laki,
    name_perempuan: user.name_perempuan,
    email: user.email,
    telp: user.telp,

});

</script>

<template>
    <div>
        <Head title="Log in" />

        <JudulNavbar></JudulNavbar>

        <div class="flex mt-[5vh] w-[100%] flex-wrap justify-center lg:justify-evenly  items-start ">
            <img :src="'storage/human.png'" alt="" class="w-[140px] mt-[-20px] z-20 rounded-full flex justify-center items-center border-[5px] p-[5px] border-white">
        </div>

        <div class="flex justify-center ">
            <div>
                <h1 class="font-bold text-center py-5 text-xl text-[#5E6282] name">{{form.name_laki}} & {{ form.name_perempuan }}</h1>
                <div class="bg-white lg:flex   py-10 rounded-lg">
                    <div class="w-[400px] px-[30px]">
                        <InputLabel for="email" value="Email" />
                        
                        
                        <TextInput
                                id="email"
                                type="email"
                                class="mt-1 block w-full"
                                v-model="form.email"
                                required
                                placeholder="Alamat Email"
                                autocomplete="username"
                            />

                            <div class="text-[12px]  pt-2 flex justify-end items-center"><img :src="'storage/iconverified.png'" alt="" class="w-[20px] mr-1">Verified</div>


                        <InputError class="mt-2" :message="form.errors.email" />
                    </div>
                    <div class="w-[400px] px-[20px]">
                        <InputLabel for="telp" value="Nomer Handphone" />

                        <TextInput
                                id="telp"
                                type="text"
                                class="mt-1 block w-full"
                                v-model="form.telp"
                                required
                                placeholder="Alamat telp"
                                autocomplete="username"
                            />

                            <div class="text-[12px]  pt-2 flex justify-end items-center"><img :src="'storage/iconnotverified.png'" alt="" class="w-[20px] mr-1"> Not Verified</div>


                        <InputError class="mt-2" :message="form.errors.telp" />
                    </div>
                </div>
                <div class="flex justify-center">
                    <ResponsiveNavLink :href="route('logout')" method="post" as="button" class="flex justify-center items-center mt-10 font-[700] text-[#707C97] ">
                            <img :src="'storage/powerlogout.png'" alt="" class="w-[20px] mr-2"> LOG OUT
                    </ResponsiveNavLink>
                </div>
            </div>
        </div>
    </div>
    <br><br><br><br>
</template>
