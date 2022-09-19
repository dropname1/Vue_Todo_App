<template>
    <div class="template">
        <div class="mainWrapper">
        <h1>Vue Todo App</h1>
        <div class="inputDiv">
             <input type="text" 
            placeholder="enter todo" 
            v-model="newTodoText"> 
            <button 
            @click="addTodo">+
            </button>
        </div>
        <div :class="{completed:todo.completed}" 
        class="todolist" v-for="(todo, index) in todos" :key="todo.id">
            <div  
            class="todoItem">{{todo.title}}</div>
            <div class="todoButtons">
                <button @click="removeTodo(todo)">completed</button>
                <button @click="deleteTodo(index)">&times;</button>
            </div>
        </div>
        </div>
    </div>
</template>

<script>
export default {
    data () {
        return {
            todos: [
                {id: 1, title: 'Leran Promise js', completed: false},
                {id: 2, title: 'Leran Router', completed: false},
                {id: 3, title: 'Leran Vuex', completed: false},
                {id: 4, title: 'Leran hooks', completed: false},
                {id: 5, title: 'Leran event loop', completed: false},
                
            ],
            newTodoText : '',
            nextTodoId: 6
        }
    },
    methods: {
        removeTodo(todo) {
            todo.completed = true
        },
        deleteTodo (index) {
            this.todos.splice(index,1)
        },
        addTodo () { 
            if (this.newTodoText) {
                this.todos.push({
                id: this.nextTodoId++, 
                title: this.newTodoText, 
                completed: false
            })
            this.newTodoText = ''
            } 
            
        }
    }

}
</script>

<style scoped>
    .template {
        background-color: #202123;
        width: 100%;
        height: 100vh;
        color: white;
        font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    }
.mainWrapper {
        width: 500px;
        display: flex;
        flex-direction: column;
        margin: 0 auto; 
    }
.todolist {
    display: flex;
    box-sizing: border-box;
    justify-content: space-between;
    width: 500px;
    border: 1px solid #343537;
    padding: 5px;
    border-radius: 5px;
    margin-bottom: 1px;
}
.todoItem {
    padding: 2px;
}
.completed {
    transition: 0.3s;
    text-decoration: line-through;
    background-color: #28292b;
}
button {
    border: none;
    background-color: transparent;
    color: rgb(207, 199, 199);
    cursor: pointer;
}
input {
    background-color: gray;
    outline: none;
    border: none;
    padding: 9px;
    border-radius: 8px;
    border-top-right-radius: 0px;
    border-bottom-right-radius: 0px;
    width: 100%;
    box-sizing: border-box;
}
.inputDiv {
    width: 500px;
    display: flex;
    margin-bottom: 20px;

}
.inputDiv button {
    font-size: 30px;
    background-color: gray;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
    padding-right: 8px;

}
</style>
