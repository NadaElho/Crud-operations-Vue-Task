<template>
        <table class="table p-2">
            <thead>
                <tr>
                <th scope="col">#</th>
                <th scope="col">Name</th>
                <th scope="col">City</th>
                <th scope="col">Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="std in students" :key="std.id">
                    <th scope="row">{{std.id}}</th>
                    <td>{{std.name}}</td>
                    <td>{{std.city}}</td>
                    <td><button class="btn btn-danger" @click="removeStudent(std)"> Remove </button></td>
                    <td><button class="btn btn-primary"  data-bs-toggle="modal" data-bs-target="#exampleModal" @click="EditStudent(std)"> Edit </button></td>
                </tr>      
                <tr>
                    <td colspan="2"># of students = {{students.length}}</td>
                    <td colspan="2"> 
                        <button type="button" class="btn btn-secondary" data-bs-toggle="modal" data-bs-target="#exampleModal">
                        Add
                        </button>
                    </td>
                </tr>         
            </tbody>
        </table>
       

        <!-- Modal -->
        <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
            <div class="modal-header">
                <h1 class="modal-title fs-5" id="exampleModalLabel" v-if="mode == 'add'">Add student</h1>
                <h1 class="modal-title fs-5" id="exampleModalLabel" v-else>Edit student</h1>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <input type="text" v-model="std.name" placeholder="name" class="mb-2"> <br/>
                <input type="text" v-model="std.city" placeholder="city">
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="addStudent(std)">Save changes</button>
            </div>
            </div>
        </div>
        </div>
       
</template>
<script>
    import {students} from '../students'
   export default{
     data:()=>({
        students,
        std:{
            name:"",
            city:""
        },
        mode: "add",
        editStudentId:''
    }),
    methods: {
        addStudent(student){
            if(this.mode == "add"){
                this.students.push({...student, id: this.students.length+1})
            }else{
                let i = this.students.findIndex((std)=> std.id == this.editStudentId)
                console.log(i);
                this.students[i]={id: this.students[i].id, ...this.std}
                this.mode = "add"
            }
            this.std={
                name:"",
                city:""
            }
            
        },
        removeStudent(student){
            let i = this.students.findIndex((std)=> std.id == student.id)
            this.students.splice(i, 1);
        },
        EditStudent(student){
            this.std={
                name: student.name,
                city: student.city
            }
            this.mode = "edit"
            this.editStudentId=student.id
        }

    },
   }
</script>
<style>
    
</style>