
<template>
<div class="w-96 mx-auto">
    <h1 class="text-lg mb-8">Post</h1>
    <div class="flex gap-5">
        <button class="w-20 hover:bg-slate-400 hover:text-white border rounded-md p-2" type="submit">Create</button>
        <Link :href="route('post.index')" class="hover:bg-white border-sky-500 border hover:text-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white">Back</Link>
    </div>
</div>
    <div class="w-96 mx-auto" v-if='post'>
        <div class="mt-8 pt-8 border-t border-gray-400">
            <div>id: {{post.id}}</div>
            <div>title: {{post.title}}</div>
            <div>content: {{post.content}}</div>
            <div class="text-sm text-right">{{post.data}}</div>
        </div>
    </div>
</template>

<script setup>
import {Link} from '@inertiajs/vue3';
import {useForm} from '@inertiajs/vue3';
import {reactive} from 'vue'
import {router} from '@inertiajs/vue3'
import {defineProps} from 'vue';

const props = defineProps({
    post: Array,
});

const form = useForm({
    name:"Index",
    components: {Link}
})



</script>
