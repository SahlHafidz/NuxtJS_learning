<template>
  <div class="py-4">
  <div class="container">
  <div class="title border-bottom d-flex align-items-center justify-content-between py-2">
    <h5>Task</h5>
    <div class="d-flex align-items-center">
      <input
      type="text"
      class="form-control"
      placeholder="Search"
      v-model="searchQuery"
      >
      <div class="d-flex align-item-center justify-content-end w-100">
      <span class="me-2">View As</span>
      <button
      class="btn btn-outline-secondary py-1 px-3"
      @click="isGrid=!isGrid" >
      {{ isGrid ? 'Grid' : 'List' }}
      </button>
    </div>
    </div>
    <div class="form-floating">
  <select class="form-select ps-5 pe-5" required name="category" v-model="dropdown" aria-label="Floating label select example">
    <label  for="floatingSelect">Works with selects</label>
    <option value="task">task</option>
    <option value="tugas">tugas</option>
    <option value="kerja">kerja</option>
  </select>
  <label for="floatingSelect">Works with selects</label>
</div>
  </div>
  <div class="list-task row">
    <!-- <CardItem :task="tasks[0]" :isGrid="isGrid" />
    <CardItem :task="tasks[1]" :isGrid="isGrid" />
    <CardItem :task="tasks[2]" :isGrid="isGrid" /> -->
    <CardItem
    v-for="(task, i) in resultdropdown "
    :key="i"
    :task="task"
    :isGrid="isGrid"
    />
  </div>
  <div class="action py-2">
    <a
      v-if="!isCreating" href="#" class="add-button"
      @click="isCreating=!isCreating">Add Task</a>
    <div v-else class="add-card">
      <div class="card mb-2">
        <div class="card-body d-flex flex-column p-0">
        <input class="form-control border-0 mb-2" placeholder="Title" type="text">
        <textarea
        class="form-control border-0 small" placeholder="Description"
        rows="3"></textarea>
        </div>
      </div>
      <div class="button-wrapper d-flex">
        <button class="btn btn-primary me-2">Save</button>
        <button
        class="btn btn-outline-secondary"
        @click="isCreating =!isCreating">Cancel</button>
      </div>
    </div>
  </div>
  </div>
  </div>
</template>
<script>
import CardItem from "@/components/Card/CardItem.vue"
export default {
  layout (context) {
    return 'custom'
  },
  components: {
    CardItem
  },
  
  data() {
    return {
      searchQuery: '',
      dropdown:null,
      
      // onchange(e){
      //   dropdown=e.target.value;
      // },
      
      // Tipe layout d  aftar task
      isGrid: true,
      // Status saat menambahkan task
      isCreating: false,
      // Daftar task
      tasks: [
        {
          title: 'Task 1',
          description: 'ini deskripsi 1',
          isDone: false,
          category:'task',
        },
        {
          title: 'Tugas 2',
          description: 'ini deskripsi 2',
          isDone: false,
          category:'tugas',
        },
        {
          title: 'Kerja 3',
          description: 'ini deskripsi 3',
          isDone: false,
          category:'kerja',
        },
      ]
    }
  },
  computed: {
    // resultQuery() {
    //   if (this.searchQuery) {
    //     return this.tasks.filter((item) => {
    //       return this.searchQuery
    //       .toLowerCase()
    //       .split(" ")
    //       .every((v) => item.title.toLowerCase().includes(v));
    //     });
    //   } else {
    //     console.log(this.tasks)
    //     return this.tasks
    //   }
    // },
    resultdropdown(){
      if (this.dropdown) {
        return this.tasks.filter((item) => {
          return this.dropdown
          .toLowerCase()
          .split(" ")
          .every((v) => item.category.toLowerCase().includes(v));
        });
      } else {
        console.log(this.tasks)
        return this.tasks
      }
}
  }
}
</script>
<style>
</style>