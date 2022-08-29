<template>
    <div class="edit">
        <EditForm />
    </div>
</template>

<script>
import EditForm from "@/components/EditForm.vue";

export default {
    name: "edit",
    components: {
        EditForm,
    },
};
</script>

<style scoped>
.edit {
    display: flex;
    justify-content: center;
    margin-top: 7em;
}
</style>
