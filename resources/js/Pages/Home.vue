<template>
    <GuestLayout>
        <div class="flex flex-col gap-y-4 items-center justify-center w-full">
            <p class="font-bold text-2xl">Welcome to My Blog</p>
            <Posts :posts="posts"/>
        </div>
    </GuestLayout>
</template>

<script>
import Posts from "@/Pages/Posts/Index.vue";
import GuestLayout from "@/Layouts/GuestLayout.vue";

export default {
    name: "Home",
    components: {
        Posts,
        GuestLayout,
    },
    props: {
        posts: Array,
    },
};
</script>
