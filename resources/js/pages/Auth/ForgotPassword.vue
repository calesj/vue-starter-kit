<script setup lang="ts">
import { Head, useForm, Link } from '@inertiajs/vue3';

const form = useForm({
    email: '',
});

function submit() {
    form.post(route('password.email'));
}
</script>

<template>
    <Head title="Forgot Password" />

    <div
        class="flex min-h-screen items-center justify-center bg-white px-4 dark:bg-zinc-950"
    >
        <div class="w-full max-w-sm">
            <div class="mb-8 text-center">
                <h1
                    class="text-2xl font-semibold text-zinc-900 dark:text-zinc-50"
                >
                    Forgot password?
                </h1>
                <p class="mt-1 text-sm text-zinc-500 dark:text-zinc-400">
                    Enter your email and we'll send you a link to reset your
                    password.
                </p>
            </div>

            <div
                v-if="$page.props.flash?.success"
                class="mb-4 rounded-md border border-green-200 bg-green-50 px-4 py-3 text-sm text-green-700 dark:border-green-800 dark:bg-green-950 dark:text-green-400"
            >
                {{ $page.props.flash.success }}
            </div>

            <form @submit.prevent="submit" class="space-y-4">
                <div>
                    <label
                        for="email"
                        class="mb-1.5 block text-sm font-medium text-zinc-700 dark:text-zinc-300"
                    >
                        Email
                    </label>
                    <input
                        id="email"
                        v-model="form.email"
                        type="email"
                        required
                        autocomplete="email"
                        placeholder="you@example.com"
                        class="w-full rounded-md border border-zinc-300 bg-white px-3 py-2 text-sm text-zinc-900 placeholder-zinc-400 transition focus:border-zinc-500 focus:ring-1 focus:ring-zinc-500 focus:outline-none disabled:opacity-50 dark:border-zinc-700 dark:bg-zinc-900 dark:text-zinc-50 dark:placeholder-zinc-500 dark:focus:border-zinc-400 dark:focus:ring-zinc-400"
                        :class="{
                            'border-red-500 focus:border-red-500 focus:ring-red-500':
                                form.errors.email,
                        }"
                    />
                    <p
                        v-if="form.errors.email"
                        class="mt-1 text-xs text-red-500"
                    >
                        {{ form.errors.email }}
                    </p>
                </div>

                <button
                    type="submit"
                    :disabled="form.processing"
                    class="w-full rounded-md bg-zinc-900 px-4 py-2 text-sm font-medium text-white transition hover:bg-zinc-700 focus:ring-2 focus:ring-zinc-500 focus:ring-offset-2 focus:outline-none disabled:opacity-50 dark:bg-zinc-50 dark:text-zinc-900 dark:hover:bg-zinc-200"
                >
                    {{ form.processing ? 'Sending...' : 'Send reset link' }}
                </button>
            </form>

            <p
                class="mt-6 text-center text-sm text-zinc-500 dark:text-zinc-400"
            >
                <Link
                    :href="route('login')"
                    class="font-medium text-zinc-700 underline underline-offset-4 hover:text-zinc-900 dark:text-zinc-300 dark:hover:text-zinc-100"
                >
                    Back to login
                </Link>
            </p>
        </div>
    </div>
</template>
