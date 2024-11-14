<template>
    <GuestLayout>
        <div class="flex flex-col w-full gap-y-4">
            <h1 class="text-2xl font-bold">Edit Post</h1>
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
                    <PrimaryButton type="submit">Update Post</PrimaryButton>
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
import { defineProps } from "vue";

const props = defineProps({
    post: Object,
});

const form = useForm({
    title: props.post?.title || "",
    body: props.post?.body || "",
    author: props.post?.author || "",
});

async function handleSubmit() {
    form.put(route("posts.update", props.post.id), {
        onSuccess: () => {
            console.log("Post updated successfully!");
        },
        onError: (error) => {
            console.error(error);
            console.error("An error occurred while updating the post.");

        },
    });
}
</script>
