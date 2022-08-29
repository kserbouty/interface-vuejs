<template>
    <div class="create">
        <CreateForm />
    </div>
</template>

<script>
import CreateForm from "@/components/CreateForm.vue";

export default {
    name: "create",
    components: {
        CreateForm,
    },
};
</script>

<style scoped>
.create {
    display: flex;
    justify-content: center;
    margin-top: 5em;
}
</style>
