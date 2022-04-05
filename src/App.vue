<template>
  <div id="app">
    <h1>Communication App</h1>
    <div class="container">
      <div class="flex">
        <FileUpload mode="basic" name="loadFiles" />

        <span class="p-float-label">
          <InputText
            class="project-name input-field"
            name="projectName"
            v-model="obj.project_name"
            type="text"
          />
          <label for="projectName">Project Name</label>
        </span>

        <span class="p-float-label">
          <InputText
            class="originator-email input-field"
            name="originatorEmail"
            v-model="obj.originator_email"
            type="text"
          />
          <label for="originatorEmail">Originator Email</label>
        </span>

        <span class="p-float-label">
          <InputText
            class="database-name input-field"
            name="databaseName"
            v-model="obj.database_name"
            type="text"
          />
          <label for="databaseName">Database Name</label>
        </span>

        <span class="p-float-label">
          <InputText
            class="sms-body input-field"
            name="smsBody"
            v-model="obj.sms_body"
            type="text"
            maxlength="164"
          />
          <label for="smsBody">SMS Body</label>
        </span>

        <div class="email-body">
          <h5>Email Body</h5>
          <Editor class="email-input" v-model="obj.email_body" />
        </div>

        <span class="p-float-label">
          <InputText
            class="sql-statement input-field"
            name="sqlStatement"
            v-model="obj.sql_body"
            type="text"
          />
          <label for="sqlStatement">SQL Statement</label>
        </span>

        <button @click="loadData()">Test Button</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      obj: {
        project_name: "",
        originator_email: "",
        database_name: "",
        sms_body: "",
        email_body: "",
        sql_body: "",
      },
    };
  },
  methods: {
    saveData() {
      const jsonData = JSON.stringify(this.obj);
      console.log(jsonData);
    },
    loadData() {
      const jsonFileData = require("./sample.json");
      this.obj.project_name = jsonFileData.project_name;
      this.obj.originator_email = jsonFileData.originator_email;
      this.obj.database_name = jsonFileData.database_name;
      this.obj.sms_body = jsonFileData.sms_body;
      this.obj.email_body = jsonFileData.email_body;
      this.obj.sql_body = jsonFileData.sql_statement;
    },
  },
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1 {
  background-color: #5286ec;
  color: white;
  text-align: center;
  margin-top: -0.4rem;
  font-size: 3rem;
}

.email-input {
  height: 18rem;
}
</style>
