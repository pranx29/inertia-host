<template>
    <GuestLayout>
        <div class="flex flex-col w-full gap-y-4">
            <h1 class="text-2xl font-bold">Create Post</h1>
            <form @submit.prevent="handleSubmit">
                <div class="mb-4">
                    <label
                        for="title"
                        class="block text-sm font-medium text-gray-700"
                    >
                        Title
                    </label>
                    <input
                        type="text"
                        name="title"
                        v-model="form.title"
                        class="mt-1 p-2 block w-full border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                    />
                </div>
                <div class="mb-4">
                    <label
                        for="author"
                        class="block text-sm font-medium text-gray-700"
                    >
                        Author
                    </label>
                    <input
                        type="text"
                        name="author"
                        v-model="form.author"
                        class="mt-1 p-2 block w-full border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                    />
                </div>
                <div class="mb-4">
                    <label
                        for="body"
                        class="block text-sm font-medium text-gray-700"
                    >
                        Body
                    </label>
                    <textarea
                        name="body"
                        v-model="form.body"
                        class="mt-1 p-2 block w-full border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                    ></textarea>
                </div>
                <div class="flex gap-x-2 mb-4">
                    <Link :href="route('home')" as="button">
                        <SecondaryButton>Cancel</SecondaryButton>
                    </Link>
                    <PrimaryButton type="submit">Create Post</PrimaryButton>
                </div>
            </form>
        </div>
    </GuestLayout>
</template>

<script setup>
import PrimaryButton from "@/Components/PrimaryButton.vue";
import SecondaryButton from "@/Components/SecondaryButton.vue";
import GuestLayout from "@/Layouts/GuestLayout.vue";
import { useForm, Link } from "@inertiajs/vue3";

const form = useForm({
    title: "",
    body: "",
    author: "",
});

async function handleSubmit() {
    form.post(route("posts.store"), {
        onSuccess: () => {
            console.log("Post created successfully!");
        },
        onError: () => {
            console.error("An error occurred while creating the post.");
        },
    });
}
</script>
