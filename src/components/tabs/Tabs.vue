<template>
  <div class="tab-form">
    <div class="list-button">
      <button
        v-for="btn in lists_btn"
        :key="btn.id"
        :class="['tab-button', { active: currentComponent === btn.component }]"
        @click="currentComponent = btn.component"
      >
        {{ btn.title }}
      </button>
    </div>
    <component :is="currentComponent" :lists="this.initResource"></component>
  </div>
</template>
<script>
import TabAdd from "./TabAdd.vue";
import TabShow from "./TabShow.vue";

export default {
  components: { TabAdd },
  name: "Tabs",
  provide() {
    return {
      addTask: this.addTask,
      deleteTask: this.deleteTask,
      deleteAll: this.deleteAll,
    };
  },
  data() {
    return {
      lists_btn: [
        {
          id: 1,
          component: TabShow,
          title: "Stored Resource",
        },
        {
          id: 2,
          component: TabAdd,
          title: "Add Resource",
        },
      ],
      currentComponent: TabShow,
      initResource: [],
    };
  },
  methods: {
    getLocalStorage(name) {
      return JSON.parse(localStorage.getItem(name));
    },
    setLocalStorage(name, data) {
      localStorage.setItem(name, JSON.stringify(data));
    },
    addTask(title, desc, link) {
      let newData = {
        title: title,
        desc: desc,
        link: link,
      };
      this.initResource.push(newData);
      localStorage.setItem("storedData", JSON.stringify(this.initResource));
      location.reload();
      setTimeout(() => this.checkButton(),100);
    },
    deleteTask(title) {
      let question = confirm("Bạn có muốn xóa không !!!!");
      if (question == true) {
        let find = this.initResource.findIndex((titleFunc) => titleFunc === title);
        this.initResource.splice(find, 1);
        localStorage.setItem("storedData", JSON.stringify(this.initResource));
      }
    },
    deleteAll() {
      let question = confirm("Bạn có muốn xóa tất cả không !!!");
      if (question == true) {
        this.initResource = [];
        localStorage.setItem("storedData", JSON.stringify(this.initResource));
      }
    },
  },
  mounted() {
    const resources = this.getLocalStorage("storedData");
    if (resources && resources.length) {
      this.initResource = resources;
      this.ButtonDel = true;
    } else {
      this.setLocalStorage("storedData", []);
    }
  },
};
</script>
<style scoped>
.list-button {
  border-radius: 12px;
  box-shadow: 0 2px 8px rgb(0 0 0 / 26%);
  padding: 1rem;
  margin: 2rem auto;
  max-width: 43.5rem;
  display: flex;
  justify-content: space-evenly;
}
.list-button button {
  outline: none;
  border: none;
  padding: 15px 20px;
  color: #c9252c;
  background-color: unset;
  display: block;
  cursor: pointer;
  font-size: 18px;
  border-radius: 10px;
  transition: 0.3s;
}
.active {
  background-color: #c9252c !important;
  color: #fff !important;
}
.list-button button:hover {
  background-color: #c54c52;
  color: #fff;
}
</style>
