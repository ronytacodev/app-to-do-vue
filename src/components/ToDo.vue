<template>
    <div class="app-container">
        <h1 class="app-header">Vue TO DO LIST </h1>

        <div class="add-task">
            <input type="text" autocomplete="off" placeholder="Add New Task" class="task-input" v-model="tasks.name"
                @keyup.enter="newItem">
            <input type="submit" value="" class="submit-task" title="Add Task" @click="newItem">
        </div>

        <ul class="task-list">
            <li class="task-list-item" v-for="task in tasks" :key="task">
                <label class="task-list-item-label">
                    <input type="checkbox">
                    <span>{{ task.name }}</span>
                </label>

                <span class="delete-btn" title="Delete Task" @click="delItem(task)">{{ task.del }}</span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'ToDo',
    data() {
        return {
            tasks: [
                { name: 'Today : Internal Meeting' },
                { name: 'Tomorrow : Read a Book' },
                { name: 'Daily :  Learn Programming' },
                { name: 'Daily :  Morning Walk' },
            ]
        }
    },

    methods: {
        newItem: function () {
            if (!this.tasks.name) {
                return
            }
            this.tasks.push({
                name: this.tasks.name,
                del: ''
            });
            this.tasks.name = "";
        },
        delItem: function (task) {
            this.tasks.splice(this.tasks.indexOf(task), 1)
        }
    }
}

</script>

<style lang="css" scoped>
input {
    outline: none;
}

ul {
    list-style: none;
    padding: 0;
}

.app-container {
    /* border: 1px solid blue; */
    max-width: 480px;
    width: 100%;
    /* width: 500px; */
    max-height: 100%;
    background-color: rgba(255, 255, 255, 0.5);
    padding: 25px;
    border-radius: 25px;
    overflow: auto;
    color: #222;
    margin-left: 5px;

}

.app-header {
    font-size: 20px;
    line-height: 32px;
    margin: 0 0 12px 0;
    color: #272727;
}

.submit-task {
    width: 32px;
    height: 32px;
    flex-shrink: 0;
    border: none;
    background: var(--add-button);
    color: #272727;
    background-image: url(@/assets/circlePlus.svg);
    background-size: 18px;
    background-position: center;
    background-repeat: no-repeat;
    border-radius: 50%;
    cursor: pointer;
    box-shadow: 0 0 12px 0 var(--add-button-shadow);
}

.add-task {
    height: 40px;
    font-size: 14px;
    display: flex;
}

.task-input {
    width: 100%;
    padding: 0 5px;
    outline: none;
    border: none;
    border-bottom: 1px solid #272727;
    background-color: transparent;
    margin-right: 15px;
    color: #272727;
    box-shadow: none;
    border-radius: 0;
}

.task-input::placeholder {
    color: #272727;
}

.task-list-item {
    /* border: 1px solid red; */
    background-color: rgba(255, 255, 255, 0.7);
    display: flex;
    align-items: center;
    border-radius: 35px;
    margin-bottom: 12px;
    width: 260px;
}

.task-list-item input {
    /* border: 2px solid orange; */
    width: 16px;
    height: 16px;
    border: 1px solid #272727;
    border-radius: 50%;
    background-image: url(@/assets/check.svg);
    /* background-image: url(assets/check.svg); */
    background-repeat: no-repeat;
    background-position: center;
    background-size: 0;
    transition: 0.2s;
    margin-right: 8px;
    /* margin-right: 5px; */
    flex-shrink: 0;
    margin-top: 4px;
    appearance: none;

}

.task-list-item input:hover {
    border-color: var(--checkbox-color);
    box-shadow: 0 0 0 3px var(--checkbox-shadow);
}

.task-list-item input:checked {
    background-size: 10px;
    border: 1px solid var(--checkbox-color);
    background-color: var(--checkbox-color);
}

.task-list-item input:checked+span {
    color: #272727;
    text-decoration: line-through #272727;
}

.task-list-item-label {
    display: flex;
    align-items: flex-start;
    color: #272727;
    margin: 8px;
    font-size: 14px;
    line-height: 24px;
    position: relative;
    transition: 0.2s;
    cursor: pointer;
}

.delete-btn {
    margin-left: auto;
    margin-right: 12px;
    display: block;
    width: 16px;
    height: 16px;
    background-image: url(@/assets/trash.svg);
    background-repeat: no-repeat;
    background-size: 16px;
    background-position: center;
    cursor: pointer;
}

@media screen and (min-width:600px) {
    .app-container {
        width: 500px;
    }

    .task-list-item {
        width: 400px;
    }
}
</style>