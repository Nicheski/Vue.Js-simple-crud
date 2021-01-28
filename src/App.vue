<template>
<div class="well clearfix">
	<fieldset class="scheduler-border">
	 <legend class="scheduler-border">Add Employee</legend>
	   <form class="form-inline">
		 <div class="form-group">


         <label for="id">ID</label>
		   <input type="text" class="form-control" id='id'  v-model='id' placeholder="ID" >
		 </div>

		 <div class="form-group">
		   <label for="name">Name</label>
		   <input type="text" id='name' class="form-control"  v-model='name' placeholder="Name">
		 </div>

		<div class="form-group">
		  <label for="age">Age</label>
		  <input type="number" id='age' class="form-control" v-model='age'  placeholder="Age"/>
		</div>

		<div class="form-group">
		  <label for="salary">Salary</label>
		  <input type="number" id='salary' class="form-control" v-model='salary' placeholder="Salary">
		</div>

		<button type="button" @click='onSubmit()' class="btn btn-primary" ><i class="glyphicon glyphicon-plus"></i>&nbsp;Add Row</button>
    
    		<button  type="button" @click='onSort()' class="btn btn-primary" ><i class="glyphicon glyphicon-plus"></i>&nbsp;Sort  By Salary</button>
	  </form>
	</fieldset>
</div>

	<div class="container" style="padding:10px 10px;">
		<h2>Vue.Js Simple Crud</h2>
      <table class="table table-bordered" id="tbl_employees">
        <thead>
          <tr>

            <th>#</th>
            <th>Name</th>
            <th>Age</th>
            <th>Salary</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody id="tbl_posts_body" >
        
          <tr v-for='inf in info'>
     
            <td><span class="sn"> {{inf.id}}</span></td>
         
            <td>{{inf.name}}</td>
            <td>{{inf.age}}</td>
            <td>{{inf.salary}}</td>
            <td><a class="btn btn-xs delete-record"><i @click="remove('item')" class="glyphicon glyphicon-trash"></i></a></td>
          </tr>
        </tbody>
      </table>
    </div>




</template>

<script>



export default {
      data(){
        return {
          id: '',
            name:'',
            age:'',
            salary: '',
            info : []

        }
    },

    methods: {
        onSubmit(){
         if(this.id || this.name || this.salary || this.age !== ''){
        this.info.push({ id:this.id, name: this.name, age: this.age, salary: this.salary  });
          }else{
            alert('Please Insert')
          }
      this.id = '',
      this.name = '',
      this.age = '',
      this.salary = ''
        
        },

        remove(item){
            this.info.splice(item, 1)
        },

        onSort(){
          this.info.sort((a,b) =>  a.salary < b.salary ? -1 : 1);
        }
    },
  name: 'App',
  components: {
   
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
