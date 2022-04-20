<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keypress.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>

        <modal :show="showModal" @close="showModal = false">
            <template #header>
                <h2>경고</h2>
            </template>
            <template #body>
                <h3>할 일을 입력하세요.</h3>
            </template>
            <template #footer>
                <span @click="showModal = false">
                    <i class="closeModalBtn fa-solid fa-check" aria-hidden="true" ></i>
                </span>
            </template>
        </modal>
    </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
    data() {
        return {
            newTodoItem: '',
            showModal: false
        }
    },

    methods: {
        addTodo() {
            if (this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                // // k, v 페어 형식
                // localStorage.setItem(value, value);
                this.$emit('addTodo', value);
                this.clearInput()
            }
            else {
                this.showModal = !this.showModal;
            }
        },
        clearInput() {
            this.newTodoItem = "";
        }

    },

    components: {
        Modal,
    }
}
</script>

<style scoped>
input:focus {
    outline: none;
}
.inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
    max-width: 500px;
    /* 인풋 박스 가운데 정렬 */
    margin-left: auto;
    margin-right: auto;
}
.inputBox input {
    border-style: none;
    font-size: 0.9rem;
    width: 80%;
}
.inputBox:focus-within {
    border: 2px solid #8763FB;
}
.addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: inline-block;
    width: 3rem;
    border-radius: 0 2.5px 2.5px 0;
}
.addBtn {
    color: white;
    vertical-align: middle;
}
</style>