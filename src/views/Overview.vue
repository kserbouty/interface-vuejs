<template>
    <div class="overview">
        <List />
    </div>
</template>

<script>
import List from "@/components/List.vue";

export default {
    name: "overview",
    components: {
        List,
    },
};
</script>

<style scoped>
.overview {
    display: flex;
    justify-content: center;
}
</style>
