<script setup>
import { Inertia } from "@inertiajs/inertia";

defineProps({
    id: String,
    blog: Object, //一件だけ取得するときはArryaではなくObjectにしないとwarningが出る
});
const deleteConfirm = (id) => {
    Inertia.delete(`/inertia/${id}`, {
        //deleteを実行する前に行いたい処理を記述
        onBefore: () => confirm("本当に削除しますか"),
    });
};
</script>

<template>
    <div>
        {{ id }}<br />
        {{ blog.title }}<br />
        <button @click="deleteConfirm(blog.id)">削除</button>
    </div>
</template>
