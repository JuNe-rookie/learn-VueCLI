<template>
  <div class="todo-footer" v-show="total">
    <label>
      <!-- <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
			<input type="checkbox" v-model="isAll"/>
    </label>
    <span>
      <span>已完成{{doneTotal}}</span> / {{total}}
    </span>
    <button class="btn btn-danger" @click="clickAll">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: 'Myfooter',
	props: ['todos', 'checkAllTodo', 'clearAllTodo'],
	computed: {
		// 全部数量
		total(){
			return this.todos.length
		},
		// 已完成数量
		doneTotal(){
			return this.todos.reduce((pre,todo)=> pre + (todo.done ? 1 : 0) ,0)
		},
		// 删除已完成任务
		// isAll(){
		// 	return this.doneTotal === this.total && this.total >0
		// }
		
		// 删除已完成任务和已完成按钮
		isAll:{
			get(){
				return this.doneTotal === this.total && this.total >0
			},
			set(value){
				this.checkAllTodo(value)
			}
		}
	},
	methods: {
		// 已完成按钮
		// checkAll(e){
		// 	// console.log(e.target.checked)
		// 	this.checkAllTodo(e.target.checked)
		// }
		clickAll(){
			this.clearAllTodo()
		}
	}
}
</script>

<style scoped>
	/*footer*/
	.todo-footer {
		height: 40px;
		line-height: 40px;
		padding-left: 6px;
		margin-top: 5px;
	}

	.todo-footer label {
		display: inline-block;
		margin-right: 20px;
		cursor: pointer;
	}

	.todo-footer label input {
		position: relative;
		top: -1px;
		vertical-align: middle;
		margin-right: 5px;
	}

	.todo-footer button {
		float: right;
		margin-top: 5px;
	}
</style>