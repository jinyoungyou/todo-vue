<template>
    <section>
        <transition-group name="list" tag="ul">
            <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="removeBtn" type="Button" @click="removeTodo(todoItem, index)">
                    <i class="fa-solid fa-trash" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>

<script>
export default {
    props: ['propsdata'],

    methods : {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
        }
    }

}
</script>

<style>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0px;
        text-align: left;
    }

    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        /* padding: 0 0.9rem; */
        background: white;
        border-radius: 5px;
        max-width: 500px;
        /* 리스트 가운데 정렬 */
        margin-left: auto;
        margin-right: auto;
    }

    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
        margin-left: 0.9rem;
    }

    .removeBtn {
        margin-left: auto;
        margin-right: 0.9rem;
        color: #de4343;
    }

    /* list transition animation */
    .list-item {
        display: inline-block;
        margin-right: 10px;
    }
    .list-move {
        transition: transform 1s;
    }
    .list-enter-active, .list-leave-active {
        transition: all 1s;
    }
    .list-enter, .list-leave-to {
        opacity: 0;
        transform: translateY(30px);
    }
</style>