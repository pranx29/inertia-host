<script>
import Header from "@/Components/Header.vue";
import { Head } from "@inertiajs/vue3";
export default {
    components: {
        Header,
        Head,
    }
};
</script>

<template>
    <Head title="Laravel" />
    <div class="min-h-screen flex justify-center m-8">
        <div class="flex items-center flex-col w-1/2">
            <Header />
            <slot />
        </div>
    </div>
</template>
