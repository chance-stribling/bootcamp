<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <Head title="Hey" />

    <div
        class="relative sm:flex sm:justify-center sm:items-center min-h-screen bg-green-400  dark:bg-green-900 selection:bg-black selection:text-white"
    >
        <div v-if="canLogin" class="sm:fixed sm:top-0 sm:right-0 p-6 text-right">
            <Link
                v-if="$page.props.auth.user"
                :href="route('dashboard')"
                >Dashboard</Link
            >

            <template v-else>
                <Link
                    :href="route('login')"
                    class="font-semibold text-black hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-green-500"
                    >Log in</Link
                >

                <Link
                    v-if="canRegister"
                    :href="route('register')"
                    class="ml-4 font-semibold text-black hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-green-500"
                    >Register</Link
                >
            </template>
        </div>
        <div>
            <Link href="/">
                <ApplicationLogo class="w-20 h-20 fill-current text-white" />
            </Link>
        </div>
        <div>
            <h1 class="font-semibold text-xl">Welcome to Bootcamp</h1>
        </div>
    </div>
</template>

<style>

</style>
