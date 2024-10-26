
<template>
<div class="w-96 mx-auto">
    <h1 class="text-lg mb-8">Posts</h1>
    <div>
        <Link :href="route('post.create')" class="hover:bg-white hover:text-sky-500 block p-2 w-32 border border-sky-500 bg-sky-500 rounded-full text-center text-white">Add post</Link>
    </div>
</div>
    <div class="w-96 mx-auto" v-if='posts'>
        <div class="mt-8 pt-8 border-t border-gray-400" v-for="post in posts">
            <div>id: {{post.id}}</div>
            <div>title: {{post.title}}</div>
            <div>content: {{post.content}}</div>
            <div class="text-sm text-right">{{post.data}}</div>
            <div class="text-sm text-right">
                <Link :href="route('post.show',post.id)" class="text-sky-500">Show</Link>
            </div>
            <div class="text-sm text-right">
                <Link :href="route('post.edit',post.id)" class="text-sky-500">Edit</Link>
            </div>
            <div class="text-sm text-right">
                <p @click="deletePost(post.id)" class="cursor-pointer text-red-500">Delete</p>
            </div>
        </div>
    </div>
</template>
<script setup>
import { Link, router, useForm } from '@inertiajs/vue3';
import { defineProps } from 'vue';

// Получаем список постов через пропсы
const props = defineProps({
    posts: Array,
});

// Функция для удаления поста
function deletePost(id) {
    if (confirm("Are you sure you want to delete this post?")) {
        router.delete(route('post.delete', id));
    }
}
</script>
