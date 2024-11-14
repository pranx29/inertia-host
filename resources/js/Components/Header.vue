<script>
import { Link } from "@inertiajs/vue3";
export default {
    components: {
        Link,
    },
};
</script>

<template>
    <header class="text-white p-4 w-full">
        <nav class="flex justify-end items-center shadow-sm">
            <ul class="flex space-x-4 py-2">
                <li>
                    <Link
                        :href="route('home')"
                        class="text-gray-500"
                        :class="{
                            'font-bold text-gray-950':
                                route().current() === 'home',
                        }"
                    >
                        Home
                    </Link>
                </li>
                <li>
                    <Link
                        :href="route('about')"
                        class="text-gray-500"
                        :class="{
                            'font-bold text-gray-950':
                                route().current() === 'about',
                        }"
                    >
                        About
                    </Link>
                </li>
            </ul>
        </nav>
    </header>
</template>
