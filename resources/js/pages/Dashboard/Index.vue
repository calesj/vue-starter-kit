<script setup lang="ts">
import { Link } from '@inertiajs/vue3';
</script>

<template>
    <div class="flex h-full items-center justify-center">
        <h1 class="text-3xl font-bold">Dashboard</h1>
    </div>
    <Link :href="route('logout')" method="post">Logout</Link>
</template>

