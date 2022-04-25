<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>

        <modal :show="showModal" @close="showModal = false">
            <h3 slot="header">경고</h3> <!-- 모달 헤더 -->
            <span slot="footer" @click="showModal = false"> <!-- 모달 푸터 -->
                할 일을 입력하세요.
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
        </modal>
    </div>
</template>

<script>
import Modal from './common/Modal.vue' // Modal.vue 불러오기

export default {
    data() {
        return {
            newTodoItem: '',
            showModal: false // 모달 동작을 위한 플래그 값
        }
    },
    methods: {
        addTodo() {
            if (this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
            } else {
                this.showModal = !this.showModal; // 텍스트 미입력 시 모달 동작
            }
        },
        clearInput() {
            this.newTodoItem = '';
        }
    },
    components: { // 모달 컴포넌트 등록
        Modal: Modal
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
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9em;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>