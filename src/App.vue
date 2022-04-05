<template>
  <div id="app">
    <h1>Communication App</h1>
    <div class="container">
    <div class="flex">
      <FileUpload mode="basic" name="loadFiles"  />

      <div class="input-field">
        <h5>Project Name</h5>
        <input 
        type="text" 
          name="project-name" 
          placeholder="Enter Project Name" 
          v-model="obj.project_name">
      </div>

      <div class="input-field">
        <h5>Originator Email</h5>
        <input 
        type="text"
           name="originator-email" 
           placeholder="Enter Originator Email"
           v-model="obj.originator_email">
      </div>

      <div class="input-field">
        <h5>Database Name</h5>
        <input 
        type="text" 
          name="project-name" 
          placeholder="Enter Database Name" 
          v-model="obj.database_name">
      </div>

    </div>
    <div class="sms-body text-area">
      <h5>SMS Body</h5>
      <textarea 
        name="smsBody" 
        id="sms-body" 
        cols="30" rows="10" 
        v-model="obj.sms_body" 
        maxlength="164"
        ></textarea>
    </div>

    <div class="email-body">
      <h5>Email Body</h5>
      <Editor 
        class="email-input" 
        v-model="obj.email_body" 
      />
    </div>

    <div class="sql-body text-area">
      <h5>Enter SQL Statement(s)</h5>
      <textarea 
        name="sqlBody" 
        id="sql-body" 
        cols="30" rows="10" 
        v-model="obj.sql_body"
      ></textarea>
    </div>

    <span class="p-float-label">
      <InputText id="username" type='text' />
      <label for="username">Username</label>
    </span>
    <button @click="saveData()">Test Button</button>
  </div>
  </div>
</template>

<script>

export default {
    data() {
        return {
            obj: {
              project_name : '',
              originator_email : '',
              database_name : '',
              sms_body : '',
              email_body : '',
              sql_body : '',

            }
        }
    },
    methods: {
        saveData(){
         const jsonData = JSON.stringify(this.obj)
         console.log(jsonData)
        },
        loadData(){
          const jsonFileData = require('./sample.json')
          this.obj.project_name = jsonFileData.project_name
          this.obj.originator_email = jsonFileData.originator_email
          this.obj.database_name = jsonFileData.database_name
          this.obj.sms_body = jsonFileData.sms_body
          this.obj.email_body = jsonFileData.email_body
          this.obj.sql_body = jsonFileData.sql_statement
        },
        
    },
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1{
  background-color: #5286EC;
  color: white;
  text-align: center;
  margin-top: -0.4rem;
  font-size: 3rem;
}

.email-input{
  height: 18rem;
}

</style>