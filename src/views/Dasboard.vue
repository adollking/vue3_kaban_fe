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
            ongoing: [],
            done: [],
            list2: [
                { id: 5, name: "Buy sarwama", color: "red" },
                { id: 6, name: "Buy burger", color: "green" },
                { id: 7, name: "Buy Cheese a", color: "blue" },
                { id: 8, name: "Buy Butterfly", color: "yellow" },
            ],
        };
    },

    methods: {
        clone({ name }) {
            return { name, id: Date.now() };
        },
        pullFunction() {
            return this.controlOnStart ? "clone" : true;
        },
        start({ originalEvent }) {
            this.controlOnStart = originalEvent.ctrlKey;
        },
        addNew() {
            this.todo.push({ id: 9, name: "Buy Butter", color: "yellow" });
        },
    }
};

</script>

<template>
    <Layout>
    </Layout>
    <div class="container">
        <div class="row mt-5">
            <div class="col-1 text-end">
                <button class="btn btn-primary btn-sm mt-4" @click="addNew()">
                    <i class="fa fa-plus"></i>
                </button>
            </div>
            <div class="col-3">
                <h3>Todo</h3>
                <draggable class="dragArea list-group" :list="todo" :group="{ name: 'people', pull: pullFunction }"
                    itemKey="name" @start="start" :clone="clone" :pull="pullFunction">
                    <template #item="{ element }">
                        <div class="list-group-item">{{ element.name }}</div>
                    </template>
                </draggable>
            </div>

            <div class="col-3">
                <h3>On going</h3>
                <draggable class="dragArea list-group" :list="ongoing" :group="{ name: 'people', pull: pullFunction }"
                    itemKey="name" @start="start" :clone="clone" :pull="pullFunction">
                    <template #item="{ element }">
                        <div class="list-group-item">{{ element.name }}</div>

                    </template>
                </draggable>
            </div>

            <div class="col-3">
                <h3>Done</h3>
                <draggable class="dragArea list-group" :list="list2" :group="{ name: 'people', pull: pullFunction }"
                    itemKey="name" @start="start" :clone="clone" :pull="pullFunction">
                    <template #item="{ element }">
                        <div class="list-group-item">{{ element.name }}</div>
                    </template>
                </draggable>
            </div>
        </div>
    </div>
</template>
