<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-md-4 offset-md-3">
          <form>
            <div class="form-group">
              <label for="todo">Todo</label>
              <input
                type="text"
                class="form-control"
                v-model="tododata.label"
              />
            </div>
            <div class="row col-md-2" style="margin: 18px;">
              <button @click="save" type="button" class="btn btn-outline-info">
                Save
              </button>
            </div>
          </form>

          <div
            class="list-group"
            v-for="eachtodo in alltodos"
            :key="eachtodo.created_at"
          >
            <a href="#" class="list-group-item list-group-item-action">
              <div class="d-flex w-100 justify-content-between">
                <h5 class="mb-1">{{ eachtodo.details  }}</h5>
                <small>{{ getDate(eachtodo.created_at) }}</small>
              </div>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export interface todo {
  details: string;
  created_at: Date;
}
export default defineComponent({
  name: "App",
  components: {},
  data() {
    return {
      name: "Sanchari",
      tododata: {
        label: "" as string
      },
      newTodo: {} as todo,
      alltodos: [] as todo[]
    };
  },
  methods: {
    save(): void {
      this.newTodo = {
        details: this.tododata?.label,
        created_at: new Date()
      };
      this.alltodos.push(this.newTodo);
    },
    getDate(unprocessedDate: Date) : string {
      let properDate = unprocessedDate.getFullYear()+'-'+(unprocessedDate.getMonth()+1)+'-'+unprocessedDate.getDate();
      return properDate
    }

  },
  computed:{
    
  }
});
</script>

