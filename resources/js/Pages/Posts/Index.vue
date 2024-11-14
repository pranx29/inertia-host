<template>
    <div class="container mx-auto">
        <div
            v-if="flash.message"
            class="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded relative mb-2"
            role="alert"
        >
            {{ flash.message }}
        </div>
        <div class="flex justify-between mb-6">
            <h1 class="text-2xl font-bold">All Posts</h1>
            <Link :href="route('posts.create')"
                ><PrimaryButton>Create Post</PrimaryButton></Link
            >
        </div>
        <div class="space-y-5">
            <div
                v-for="post in posts"
                :key="post.id"
                class="flex flex-col gap-y-2 border border-gray-300 rounded-md shadow-xs p-4 w-full"
            >
                <div>
                    <Link
                        :href="route('posts.show', { id: post.id })"
                        class="font-bold hover:underline"
                        >{{ post.title }}</Link
                    >
                    <p class="text-sm text-gray-500">{{ post.author }}</p>
                </div>
                <p>{{ post.body }}</p>
                <div class="flex gap-x-2">
                    <Link :href="route('posts.edit', { id: post.id })">
                        <PrimaryButton>Edit</PrimaryButton>
                    </Link>
                    <SecondaryButton @click="handleDeletePost(post.id)"
                        >Delete</SecondaryButton
                    >
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { defineProps, computed } from "vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import SecondaryButton from "@/Components/SecondaryButton.vue";
import { Link, router, usePage } from "@inertiajs/vue3";

const props = defineProps({
    posts: Array,
});

const flash = computed(() => usePage().props.flash);

const handleDeletePost = (id) => {
    const isConfirmed = confirm("Are you sure you want to delete this post?");
    if (!isConfirmed) {
        return;
    }
    try {
    router.delete(route("posts.destroy", id));
    } catch (error) {
        console.error(error);
    }
};
</script>
