<script setup>
import { Head } from '@inertiajs/vue3';
import PageLayout from './PageLayout.vue';
</script>

<template>
    <Head title="About Page" />

    <PageLayout>
        <div class="max-w-2xl mx-auto mt-8 p-6 bg-white rounded-3xl shadow-lg">
            <h1 class="text-3xl font-bold text-gray-800 mb-6">About Me</h1>

            <div class="space-y-4">
                <div class="flex items-center space-x-4">
                    <span class="text-lg font-semibold text-gray-700">Name:</span>
                    <p class="text-lg text-gray-600">John Axcel A. Cervantes</p>
                </div>
                <div class="flex items-center space-x-4">
                    <span class="text-lg font-semibold text-gray-700">Course & Year:</span>
                    <p class="text-lg text-gray-600">BSIT - 3</p>
                </div>
                <div class="flex items-center space-x-4">
                    <span class="text-lg font-semibold text-gray-700">Cell No.:</span>
                    <p class="text-lg text-gray-600">09467615056</p>
                </div>
            </div>
        </div>
    </PageLayout>
</template>
