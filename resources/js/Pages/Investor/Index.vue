<script setup>
import { Head, router } from '@inertiajs/vue3';
import PageLayout from '../PageLayout.vue';

const props = defineProps({
    investors: Object,
});

function goToCreatePage() {
    router.visit('/investors/create');
}
</script>

<template>
    <Head title="Investors" />
    <PageLayout>
        <div class="flex flex-col md:flex-row p-4 justify-between items-start md:items-center mb-8 gap-4">
            <h1 class="text-3xl font-bold text-white">📊 Investors</h1>
            <button
                @click="goToCreatePage"
                class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-5 rounded-xl transition-all shadow-md"
            >
                ➕ Add Investor
            </button>
        </div>

        <div class="grid grid-cols-1 p-4 sm:grid-cols-2 lg:grid-cols-4 gap-6">
            <div
                v-for="investor in investors.data"
                :key="investor.id"
                class="rounded-2xl border border-gray-200 shadow-sm hover:shadow-md transition bg-white p-6"
            >
                <h2 class="text-xl font-semibold text-gray-800 mb-2">
                    {{ investor.last_name }}, {{ investor.first_name }}
                </h2>
                <div class="text-gray-600 space-y-1 text-sm">
                    <p><span class="font-medium">📞 Phone:</span> {{ investor.phone }}</p>
                    <p><span class="font-medium">🏠 Address:</span> {{ investor.address }}</p>
                    <p><span class="font-medium">💼 Investment Type:</span> {{ investor.investment_type }}</p>
                </div>
            </div>
        </div>

        <div class="mt-10 pb-5 flex justify-center">
            <div class="flex gap-3">

                <button
                    :disabled="investors.current_page === 1"
                    @click="$inertia.visit(investors.first_page_url)"
                    class="px-5 py-2 rounded-lg text-sm font-medium transition
                        bg-gray-200 text-gray-700 hover:bg-gray-300
                        disabled:opacity-50 disabled:cursor-not-allowed"
                >
                    ⏮️ First
                </button>

                <button
                    :disabled="!investors.prev_page_url"
                    @click="$inertia.visit(investors.prev_page_url)"
                    class="px-5 py-2 rounded-lg text-sm font-medium transition
                        bg-gray-200 text-gray-700 hover:bg-gray-300
                        disabled:opacity-50 disabled:cursor-not-allowed"
                >
                    ⬅️ Previous
                </button>

                <button
                    :disabled="!investors.next_page_url"
                    @click="$inertia.visit(investors.next_page_url)"
                    class="px-5 py-2 rounded-lg text-sm font-medium transition
                        bg-gray-200 text-gray-700 hover:bg-gray-300
                        disabled:opacity-50 disabled:cursor-not-allowed"
                >
                    Next ➡️
                </button>

                <button
                    :disabled="investors.current_page === investors.last_page"
                    @click="$inertia.visit(investors.last_page_url)"
                    class="px-5 py-2 rounded-lg text-sm font-medium transition
                        bg-gray-200 text-gray-700 hover:bg-gray-300
                        disabled:opacity-50 disabled:cursor-not-allowed"
                >
                    Last ⏭️
                </button>
            </div>
        </div>

    </PageLayout>
</template>
