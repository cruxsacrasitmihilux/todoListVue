<template>
      <b-form>
        <b-form-group
          label="Título"
          label-for="subject"
          class="texto"
        >
          <b-form-input
            id="subject"
            v-model="formAddTask.subject"
            type="text"
          
            required
            autocomplete="off"
          ></b-form-input>
        </b-form-group>

        <b-form-group
          label="Descrição"
          label-for="description"
          class="texto"
        >
          <b-form-textarea
            id="description"
            v-model="formAddTask.description"
            type="text"

            required
            autocomplete="off"
          ></b-form-textarea>
        </b-form-group>

        <b-button type="submit" variant="outline-secondary" @click="saveTask"> Salvar </b-button>
      </b-form>
</template>

<script>
import ToastMixin from "@/mixins/toastMixin.js";

export default {
  name: "formAddTask",

  mixins: [ToastMixin],

  data() {
    return {
      formAddTask: {
        subject: "",
        description: ""
      },
      methodSave: "new"
    }
  },

  created() {
    if(this.$route.params.index === 0 || this.$route.params.index !== undefined){
      this.methodSave = "update";
      let tasks = JSON.parse(localStorage.getItem("tasks"));
      this.formAddTask = tasks[this.$route.params.index];
    }
  },

  methods: {
    saveTask() {
      if(this.methodSave === "update"){
        let tasks = JSON.parse(localStorage.getItem("tasks"));
        tasks[this.$route.params.index] = this.formAddTask;
        localStorage.setItem("tasks", JSON.stringify(tasks));
        this.showToast("success", "Sucesso!", "Tarefa atualizada com suceso");
        this.$router.push({ name: "list" });
        return;
      }

      let tasks = (localStorage.getItem("tasks")) ? JSON.parse(localStorage.getItem("tasks")) : [];
      tasks.push(this.formAddTask);
      localStorage.setItem("tasks", JSON.stringify(tasks));
      this.showToast("success", "Sucesso!", "Tarefa criada com suceso");
      this.$router.push({ name: "list" });
    }
  }
}
</script>

<style>
  .container{
    height: calc(100vh - 64px);
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    padding-top: 30px;
  }
  .texto{
    color: rgb(255, 201, 5, 1);
    font-weight: 600;
  }
  #description, #subject{
    background-color: #292929;
    border-radius: 7px;
    color: rgb(255, 201, 5, 1);
    box-shadow: -1px 1px 11px 1px rgba(255, 201, 5, 1);
    -webkit-box-shadow: -1px 1px 11px 1px rgba(255, 201, 5, 1);
    border: none;
}
</style>

