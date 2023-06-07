<script setup>
    import { Link } from '@inertiajs/inertia-vue3';

    import{ ref } from 'vue';

const newTitle = ref('')
const newContent = ref('')
</script>

<template>
    Inertiaテスト<br>
    <a href="/">aタグ経由</a><br>
    <Link href="/">Linkタグ経由</Link><br>
    <Link v-bind:href="route('inertia.index')">名前付きルートの確認</Link><br>
    <Link :href="route('inertia.show', {id: 50})">ルートパラメータテスト</Link>

    <div class="md-8"></div>
    <input type="text" name="newTitle" v-model="newTitle"><br>
    <input type="text" name="newContent" v-model="newContent"><br>
    <Link as="button" method="post" :href="route('inertia.store')"
     :data="{
        title: newTitle,
        content: newContent
     }">DB保存テスト</Link>
</template>