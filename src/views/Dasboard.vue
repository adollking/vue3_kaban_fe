<script>
import Layout from "@/router/layouts/main.vue";
import draggable from "vuedraggable";

export default {
    name: "Dashboard",
    components: {
        Layout,
        draggable,
    },
    data() {
        return {
            todo: [
                { id: 1, name: "Buy Milk", color: "red" },
                { id: 2, name: "Buy Bread", color: "green" },
                { id: 3, name: "Buy Cheese", color: "blue" },
                { id: 4, name: "Buy Butter", color: "yellow" },
            ],
            list2: [
                { id: 5, name: "Buy Milk", color: "red" },
                { id: 6, name: "Buy Bread", color: "green" },
                { id: 7, name: "Buy Cheese", color: "blue" },
                { id: 8, name: "Buy Butter", color: "yellow" },
            ],
        };
    },

    methods: {
        clone({ name }) {
            return { name, id: idGlobal++ };
        },
        pullFunction() {
            return this.controlOnStart ? "clone" : true;
        },
        start({ originalEvent }) {
            this.controlOnStart = originalEvent.ctrlKey;
        }
    }
};

</script>

<template>
    <Layout>
    </Layout>
    <div class="mb-4">
        <b-avatar></b-avatar>
        <b-avatar variant="primary" text="BV"></b-avatar>
        <b-avatar variant="info" src="https://placekitten.com/300/300"></b-avatar>
        <b-avatar variant="success" icon="people-fill"></b-avatar>
    </div>

    <div class="container">
        <div class="row mt-5">
            <div class="col-3">
                <h3>Todo</h3>
                <draggable class="list-group" :list="todo" group="people" itemKey="name">
                    <template #item="{ element, index }">
                        <div class="list-group-item">{{ element.name }} {{ index }}</div>
                    </template>
                </draggable>
            </div>

            <div class="col-3">
                <h3>On going</h3>
                <draggable class="list-group" :list="list2" group="people" @change="log" itemKey="name">
                    <template #item="{ element, index }">
                        <div class="list-group-item">{{ element.name }} {{ index }}</div>
                    </template>
                </draggable>
            </div>
        </div>
    </div>
</template>
