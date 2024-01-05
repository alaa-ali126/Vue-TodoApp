<template>
  <div class="tasks-container">
    <div class="date-container">
      <div class="date">
        <span class="day">{{ day }}</span>
        <div class="years-mounth">
          <span class="mounth">{{ mounth }}</span>
          <span class="year">{{ year }}</span>
        </div>
      </div>
      <div class="week-day">{{ weekDay }}</div>
    </div>
    <div class="task-item-container">
      <TasksItem
        :key="task.id"
        v-for="task in isCompleted"
        :task="task"
        v-model="task.isCompleted"
        @removeItem="removeItem"
        @updateLocalStorage="updateLocalStorage"></TasksItem>
      <TasksItem
        :key="task.id"
        v-for="task in inProgress"
        :task="task"
        v-model="task.isCompleted"
        @removeItem="removeItem"
        @updateLocalStorage="updateLocalStorage"></TasksItem>
    </div>
    <button class="button-68" role="button" @click="addTask">
      <i class="fa-solid fa-plus"></i>
    </button>
    <input type="text" class="add" v-model="text" @keyup="addByEnter" />
    <div v-if="errorMsg" class="error-msg">
      <i class="fa fa-times-circle"></i>
      Pleas Add Some Text
    </div>
  </div>
</template>

<script>
import TasksItem from "./TasksItem.vue";
export default {
  data() {
    return {
      day: Number,
      weekDay: String,
      mounth: String,
      year: Number,
      text: "",
      tasks:
        JSON.parse(localStorage.getItem("todos")) == null
          ? []
          : JSON.parse(localStorage.getItem("todos")),
      errorMsg: false,
    };
  },
  created() {
    const daysOfWeek = [
      "Sunday",
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday",
    ];
    const date = new Date();
    this.year = date.getFullYear();
    this.mounth = date
      .toLocaleString("default", { month: "short" })
      .toUpperCase();
    this.day = date.getDate();
    this.weekDay = daysOfWeek[date.getDay()];
  },
  methods: {
    addTask() {
      if (this.text.trim() === "") {
        this.errorMsg = true;
        return;
      } else {
        this.tasks.push({
          id: new Date().getTime(),
          title: this.text,
          isCompleted: false,
        });
        this.errorMsg = false;
      }
      this.text = "";
      this.updateLocalStorage();
    },
    removeItem(data) {
      this.tasks.splice(this.tasks.indexOf(data), 1);
      this.updateLocalStorage();
    },
    addByEnter() {
      if (event.keyCode === 13) {
        this.addTask();
      }
    },
    updateLocalStorage(data) {
      data.id = new Date().getTime();
      this.tasks.sort((x, y) => (x.id > y.id ? 1 : x.id < y.id ? -1 : 0));
      localStorage.setItem("todos", JSON.stringify(this.tasks));
    },
  },

  components: {
    TasksItem,
  },
  computed: {
    inProgress() {
      return this.tasks.filter((task) => !task.isCompleted);
    },
    isCompleted() {
      return this.tasks.filter((task) => task.isCompleted);
    },
  },
};
</script>

<style>
.tasks-container {
  position: absolute;
  width: 400px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  padding: 40px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  border-radius: 6px;
}

.tasks-container .date-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 600;
  margin-bottom: 40px;
}

.tasks-container .date-container .date {
  display: flex;
  align-items: center;
}

.tasks-container .date .day {
  font-size: 2.7em;
  font-weight: 700;
}

.tasks-container .date .years-mounth {
  display: flex;
  flex-direction: column;
  margin-left: 10px;
}

.tasks-container .date .mounth {
  font-weight: 700;
}

.tasks-container .date-container .week-day {
  font-weight: 900;
  font-size: 1.1em;
}

.button-68 {
  appearance: none;
  backface-visibility: hidden;
  background-color: #50e3a4;
  border-radius: 50%;
  border-style: none;
  box-shadow: rgba(39, 174, 96, 0.15) 0 4px 9px;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: Inter, -apple-system, system-ui, "Segoe UI", Helvetica, Arial,
    sans-serif;
  font-size: 16px;
  font-weight: 600;
  letter-spacing: normal;
  line-height: 1.5;
  outline: none;
  overflow: hidden;
  padding: 13px 20px;
  position: absolute;
  text-align: center;
  text-decoration: none;
  transform: translate3d(0, 0, 0);
  transition: all 0.3s;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: top;
  white-space: nowrap;
  width: 65px;
  height: 65px;
  left: 50%;
  bottom: calc(-65px / 2);
  transform: translateX(-50%);
}
.button-68:hover {
  background-color: #3bca8c;
  opacity: 1;
  transition-duration: 0.35s;
}
.button-68:hover {
  box-shadow: rgba(39, 174, 96, 0.2) 0 6px 12px;
}

.add {
  margin: 20px 0;
  display: block;
  width: 100%;
  border: 2px solid #50e3a394;
  border-radius: 6px;
  padding: 10px;
  outline: none;
  transition: 0.3s;
}

.add:focus {
  border-color: #3bca8c;
}

.error-msg {
  margin: 10px 0;
  padding: 10px;
  border-radius: 3px 3px 3px 3px;
  color: #d8000c;
  background-color: #ffbaba;
}
</style>
