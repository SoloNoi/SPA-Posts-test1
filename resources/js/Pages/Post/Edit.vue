<template>
    <h1 class="text-lg mb-2">Edit</h1>
    <div class="mt-10 flex flex-col items-center m-auto">
        <form class="flex flex-col gap-5" @submit.prevent="update">
            <label for="title">Title:</label>
            <input class="w-56 outline-none rounded-md" id="title" v-model="form.title" placeholder="Title"/>
            <label for="content">Content:</label>
            <textarea class="w-56 outline-none rounded-md" id="content" v-model="form.content" placeholder="Content"/>

            <div class="flex gap-5">
                <button class="w-20 hover:bg-slate-400 hover:text-white border rounded-md p-2" type="submit">Update</button>
                <Link :href="route('post.index')" class="hover:bg-white border-sky-500 border hover:text-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white">Back</Link>
            </div>
        </form>
    </div>
</template>

<script setup>
import {Link} from '@inertiajs/vue3';
import {defineProps} from 'vue';
import {router} from '@inertiajs/vue3'
import {reactive} from 'vue'

// Определение пропсов для получения данных поста
const props = defineProps({
    postToShow: Object,
})

// Инициализация формы с данными поста
const form = reactive({
    id: props.postToShow.id,
    title: props.postToShow.title ,
    content: props.postToShow.content ,
});

// Функция для обновления поста
function submit() {
    router.post('/posts', form)
}
</script>
