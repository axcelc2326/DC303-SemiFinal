<script setup>
import { Head, useForm } from '@inertiajs/vue3';
import PageLayout from '../PageLayout.vue';

const form = useForm({
    first_name: '',
    last_name: '',
    phone: '',
    address: '',
    investment_type: '',
});

const submit = () => {
    form.post('/investors');
};
</script>

<template>
    <Head title="Add Investor" />
    <PageLayout>
        <div class="max-w-2xl mx-auto">

            <div class="mb-6 pt-5 flex justify-between items-center">
                <h1 class="text-3xl font-bold text-white">📝 Create New Investor</h1>

                <button
                    @click="$inertia.visit('/investors')"
                    type="button"
                    class="inline-flex items-center gap-2 bg-blue-600 hover:bg-blue-700 text-white font-semibold px-4 py-2 rounded-lg transition font-medium"
                >
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                    </svg>
                    Back to Investors
                </button>
            </div>


            <form @submit.prevent="submit" class="space-y-6 bg-white p-4 rounded-2xl shadow-md border border-gray-200">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div>
                        <label class="block text-sm font-medium text-black mb-1">First Name</label>
                        <input
                            v-model="form.first_name"
                            type="text"
                            class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                        />
                        <p v-if="form.errors.first_name" class="text-red-500 text-xs mt-1">{{ form.errors.first_name }}</p>
                    </div>

                    <div>
                        <label class="block text-sm font-medium text-black mb-1">Last Name</label>
                        <input
                            v-model="form.last_name"
                            type="text"
                            class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                        />
                        <p v-if="form.errors.last_name" class="text-red-500 text-xs mt-1">{{ form.errors.last_name }}</p>
                    </div>

                    <div>
                        <label class="block text-sm font-medium text-black mb-1">Phone</label>
                        <input
                            v-model="form.phone"
                            type="text"
                            class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                        />
                        <p v-if="form.errors.phone" class="text-red-500 text-xs mt-1">{{ form.errors.phone }}</p>
                    </div>

                    <div>
                        <label class="block text-sm font-medium text-black mb-1">Address</label>
                        <input
                            v-model="form.address"
                            type="text"
                            class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                        />
                        <p v-if="form.errors.address" class="text-red-500 text-xs mt-1">{{ form.errors.address }}</p>
                    </div>
                </div>

                <div>
                    <label class="block text-sm font-medium text-black mb-1">Investment Type</label>
                    <select
                        v-model="form.investment_type"
                        class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                    >
                        <option value="">Select one</option>
                        <option value="micro">Micro</option>
                        <option value="sponsor">Sponsor</option>
                        <option value="benefactor">Benefactor</option>
                    </select>
                    <p v-if="form.errors.investment_type" class="text-red-500 text-xs mt-1">{{ form.errors.investment_type }}</p>
                </div>

                <div class="pt-4">
                    <button
                        type="submit"
                        class="w-full md:w-auto bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-6 rounded-xl transition-all shadow-md"
                    >
                        ➕ Submit Investor
                    </button>
                </div>
            </form>
        </div>
    </PageLayout>
</template>
