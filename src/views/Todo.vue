<template>
  <div class="home">

    <v-list>
      
      <v-row no-gutters align="center" class="ma-4">
        <v-col cols="8">
          <div>
            <template>
              <v-form>
                <v-container>
                  <v-text-field 
                    v-model="newTask"
                    clearable
                    ref="inputRef"
                    >
                    <template v-slot:label>
                      What shall we do today? <v-icon style="vertical-align: middle">
                        mdi-feather
                      </v-icon>
                    </template>
                  </v-text-field>
                </v-container>
              </v-form>
            </template>
          </div>
        </v-col>

        <v-col style="margin: 1em;">
          <div class="text-center">
            <v-btn
              rounded
              color="blue lighten-3 black--text"
              dark

              @click="addTask()"
            >
              Add Task
            </v-btn>
          </div>
        </v-col>
        </v-row>
     </v-list>
     
      
      <v-dialog
        v-model="dialog"
        max-width="400"
      >
        <v-card>
          <v-card-title class="text-h5">
            Edit item:  <strong>{{toEdit.title}}</strong>
          </v-card-title>

           <v-text-field class="ma-4"
            clearable
            ref="editRef"
            label="type here"
            v-model="editedTitle"
          ></v-text-field>

          <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn
              color="green darken-1"
              text
              @click="dialog=false"
            >
              Cancel
            </v-btn>

            <v-btn
              color="green darken-1"
              text
              @click="editTask(toEdit)"
            >
              Okay
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>

    <v-list flat pt-0>
    <div v-for="task in tasks" v-bind:key="task.id">
     <v-list-item
      @click="doneTask(task.id)"
      :class="{'blue lighten-5': task.done}"
     >
        <template v-slot:default>
          <v-list-item-action>
            <v-checkbox :input-value="task.done" colors="primary"></v-checkbox>
          </v-list-item-action>
       
          <v-list-item-content>
            <v-list-item-title
              :class="{'text-decoration-line-through' : task.done}"
            >
              {{task.title}}
            </v-list-item-title>
          </v-list-item-content>

          <v-btn
            rounded
          >
            <v-icon 
            color="grey lighten-1"
            @click="dialog=true, task.done = !task.done, toEdit = task">
              mdi-lead-pencil
            </v-icon>
          </v-btn>

          <v-list-item-action>
            <v-btn icon
              @click="deleteTask(task.id)"
            >
              <v-icon color="grey lighten-1">
                mdi-trash-can-outline
              </v-icon>
            </v-btn>
          </v-list-item-action>

        


        </template>
      </v-list-item>
      <v-divider></v-divider>
    </div>
     
    

    </v-list>
  </div>
  
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      dialog: false,
      editedTitle: null,
      toEdit: [],
      newTask: null,
      tasks: [
      ]
    }
  },
  methods:{
    doneTask(id){
      let tasks = this.tasks
      tasks= this.tasks.filter(task => task.id === id)[0]
      tasks.done = !tasks.done
    },
    deleteTask(id){
      this.tasks= this.tasks.filter(del => del.id !== id)
    },
    addTask(){
      if(this.newTask !== null){
        let newId = this.tasks.length + 1
        this.tasks.push({id: newId, title: this.newTask, done: false})
        
        //clear field
        this.newTask = null
        this.$refs.inputRef.clearableCallback()
      }
    },
    editTask(toEdit){
      if(this.editedTitle !== null){
        this.dialog = false 
        let index = 0
        this.tasks.forEach(task => {
          if(task.id === toEdit.id){
            this.tasks[index].title = this.editedTitle
          }
          index+=1
        });

        //clear field
        
        this.editedTitle = null
        this.$refs.editRef.clearableCallback() 
      }
      
      
    }  
  }
}
  
</script>
