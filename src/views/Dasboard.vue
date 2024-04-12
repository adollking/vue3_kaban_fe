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
            ongoing: [
                { id: 1, name: "going to jatim park", color: "red" },
            ],
            done: [
                { id: 5, name: "Buy sarwama", color: "red" },
                { id: 6, name: "Buy burger", color: "green" },
                { id: 7, name: "Buy Cheese a", color: "blue" },
                { id: 8, name: "Buy Butterfly", color: "yellow" },
            ],
            modal1: false,
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
        deleteItem(tipe, index) {
            if (tipe === "todo") {
                this.todo.splice(index, 1);
            } else if (tipe === "ongoing") {
                this.ongoing.splice(index, 1);
            } else {
                this.done.splice(index, 1);
            }
        },
    }
};

</script>

<template>
    <Layout />
    <div class="container">
        <div class="row mt-5">
            <div class="col-1 text-end">
                <button class="btn btn-primary btn-sm mt-4" @click="this.modal1 = true">
                    <i class="fa fa-plus"></i>
                </button>
            </div>
            <div class="col-3">
                <h3>Todo</h3>
                <draggable class="dragArea list-group" :list="todo" :group="{ name: 'people', pull: pullFunction }"
                    itemKey="name" @start="start" :clone="clone" :pull="pullFunction">
                    <template #item="{ element, index }">
                        <div class="list-group-item">{{ element.name }}
                            <span class="float-end">
                                <i class="fa fa-trash-can danger" @click="deleteItem('todo', index)"></i>
                            </span>
                        </div>
                    </template>
                </draggable>
            </div>

            <div class="col-3">
                <h3>On going</h3>
                <draggable class="dragArea list-group" :list="ongoing" :group="{ name: 'people', pull: pullFunction }"
                    itemKey="name" @start="start" :clone="clone" :pull="pullFunction">
                    <template #item="{ element, index }">
                        <div class="list-group-item">{{ element.name }}
                            <span class="float-end">
                                <i class="fa fa-trash-can danger" @click="deleteItem('ongoing', index)"></i>
                            </span>
                        </div>
                    </template>
                </draggable>
            </div>

            <div class="col-3">
                <h3>Done</h3>
                <draggable class="dragArea list-group" :list="done" :group="{ name: 'people', pull: pullFunction }"
                    itemKey="name" @start="start" :clone="clone" :pull="pullFunction">
                    <template #item="{ element, index }">
                        <div class="list-group-item">{{ element.name }}
                            <span class="float-end">
                                <i class="fa fa-trash-can danger" @click="deleteItem('done', index)"></i>
                            </span>
                        </div>
                    </template>
                </draggable>
            </div>
        </div>
    </div>
</template>
