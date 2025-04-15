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
            <h1 class="text-3xl font-bold p-4 text-white mb-8">📝 Create New Investor</h1>

            <form @submit.prevent="submit" class="space-y-6 bg-white p-4 rounded-2xl shadow-md border border-gray-200">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- First Name -->
                    <div>
                        <label class="block text-sm font-medium text-black mb-1">First Name</label>
                        <input
                            v-model="form.first_name"
                            type="text"
                            class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                        />
                        <p v-if="form.errors.first_name" class="text-red-500 text-xs mt-1">{{ form.errors.first_name }}</p>
                    </div>

                    <!-- Last Name -->
                    <div>
                        <label class="block text-sm font-medium text-black mb-1">Last Name</label>
                        <input
                            v-model="form.last_name"
                            type="text"
                            class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                        />
                        <p v-if="form.errors.last_name" class="text-red-500 text-xs mt-1">{{ form.errors.last_name }}</p>
                    </div>

                    <!-- Phone -->
                    <div>
                        <label class="block text-sm font-medium text-black mb-1">Phone</label>
                        <input
                            v-model="form.phone"
                            type="text"
                            class="w-full border-gray-300 focus:border-blue-500 focus:ring-blue-500 rounded-lg shadow-sm text-sm"
                        />
                        <p v-if="form.errors.phone" class="text-red-500 text-xs mt-1">{{ form.errors.phone }}</p>
                    </div>

                    <!-- Address -->
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

                <!-- Investment Type -->
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

                <!-- Submit -->
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
