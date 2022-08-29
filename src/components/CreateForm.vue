<template>
    <div class="create-form">
        <div class="card border-dark bg-dark mb-3">
            <div class="card-header text-white bg-dark">Create Product</div>
            <div class="card-body text-white bg-secondary">
                <div class="form-group">
                    <label for="Name">Product name *</label>
                    <input
                        v-model="name"
                        type="text"
                        class="form-control"
                    />
                    <div class="form-group">
                        <label for="">Description</label>
                        <textarea
                            v-model="description"
                            class="form-control"
                            rows="2"
                        ></textarea>
                    </div>
                    <div class="form-row">
                        <div class="form-group col-md-6">
                            <label for="Quantity">Quantity</label>
                            <input
                                v-model.number="quantity"
                                type="number"
                                class="form-control"
                                id="quantity"
                            />
                        </div>
                        <div class="form-group col-md-6">
                            <label for="Price">Price</label>
                            <input
                                v-model.number="price"
                                type="number"
                                class="form-control"
                                id="price"
                            />
                        </div>
                    </div>
                    <div class="button-group">
                        <router-link
                            type="button"
                            class="btn btn-light"
                            :to="{
                                name: 'overview',
                            }"
                            tag="button"
                            >Cancel</router-link
                        >
                        <button
                            @click="createProduct()"
                            type="button"
                            class="btn btn-success"
                        >
                            Create
                        </button>
                    </div>
                </div>
            </div>
            <div class="card-footer bg-dark text-muted">
                <small class="form-text text-white">
                    * The product name is mandatory.
                </small>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "CreateForm",
    data() {
        return {
            name: "",
            description: "",
            quantity: 0,
            price: 0,
            error: [],
        };
    },
    methods: {
        createProduct() {
            axios
                .post("http://localhost:8000/api/json/create", {
                    name: this.name,
                    description: this.description,
                    quantity: this.quantity,
                    price: this.price,
                })
                .then(function (response) {
                    alert(response.data);
                    location.replace("/");
                })
                .catch((error) => {
                    alert(error.response.data);
                });
        },
    },
};
</script>

<style scoped>
.create-form {
    margin: 4em;
    width: 55%;
}

button {
    margin: 1.7em 0.7em;
}

.button-group {
    display: flex;
    justify-content: center;
    margin-top: 2em;
}

.card-header,
.card-footer {
    text-align: center;
}

.card-body {
    padding: 1em 4em;
}

.form-row {
    padding-left: 3em;
}

.form-group label {
    margin-top: 2em;
}

#quantity,
#price {
    width: 75%;
}
</style>