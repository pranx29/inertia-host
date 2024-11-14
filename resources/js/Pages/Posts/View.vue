<template>
    <GuestLayout>
        <div>
            <div>
                <p class="font-bold">{{ post.title }}</p>
                <p class="text-sm text-gray-500">{{ post.author }}</p>
            </div>
            <p>{{ post.body }}</p>
            q
        </div>
    </GuestLayout>
</template>

<script setup>
import GuestLayout from "@/Layouts/GuestLayout.vue";
import { defineProps } from "vue";

const props = defineProps({
    post: Array,
});
</script>
