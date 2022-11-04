<template>
    <body>
        <nav style="height: 50px">
      <li>
        <div>
          <b-button v-b-toggle.sidebar-1 vertical class="d-block p-3 link-danger text-decoration-none" >Sidebar</b-button>
          <b-sidebar id="sidebar-1" title="Sidebar" shadow>
            <nav class="mb-3">
            <b-nav vertical>
              <b-nav-item href="#" @click="hide">Home</b-nav-item>
              <b-nav-item href="#" @click="hide">All Students</b-nav-item>
              <b-nav-item href="#" @click="hide">About Page</b-nav-item>
              <b-nav-item href="#" @click="hide">Privacy and Settings</b-nav-item>
            </b-nav>
          </nav>
          </b-sidebar>
        </div>
      </li>
      <li style="float:right"><a href="/" class="d-block p-3 link-danger text-decoration-none" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Icon-only">
      <svg class="bi" width="40" height="1px"><use xlink:href="#bootstrap"></use></svg>
      <span class="visually-hidden">Logout</span>
    </a></li>
     </nav>
     

     <div class="container">
    <br>
    <div class="form-inline" action="#">
    <input type="text" id="form-name" v-model="item.name" placeholder="StudentName" class="form-control">
    <input type="text" id="form-Add" v-model="item.Add" placeholder="StudentAddress" class="form-control">
    <input type="date" id="form-Dob" v-model="item.Dob" placeholder="DateOfBirth(mm/dd/yy)" class="form-control">
    <input type="text" v-model="item.desc" placeholder="StudentCourse" class="form-control" v-on:keyup.enter="addItem">
    <button @click="addItem" class="btn btn-dark">Add on Item<i class="fas fa-plus"></i></button>
      </div>
    <br><br>
    <table class="table table-striped table-bordered table-sm">
      <thead class="thead-light">
        <th>Student Name</th>
        <th>StudentAdd</th>
        <th>DateOfBirth</th>
        <th>Course</th>
        <th class="col-3">Edit/Del</th>
      </thead>
      <tr v-for="item in items" :key="item.name">
        <td>
          <input v-if="item.edit" type="text" v-model="item.name"  v-on:keyup.enter="item.edit = !item.edit">
          <span v-else>{{item.name}} </span>
        </td>
        <td>
          <input v-if="item.edit" type="text" v-model="item.Add"  v-on:keyup.enter="item.edit = !item.edit">
          <span v-else>{{item.Add}} </span>
        </td>
        <td>
          <input v-if="item.edit" type="text" v-model="item.Dob"  v-on:keyup.enter="item.edit = !item.edit">
          <span v-else>{{item.Dob}} </span>
        </td>
        <td>
          <input v-if="item.edit" type="text" v-model="item.desc" v-on:keyup.enter="item.edit = !item.edit">
          <span v-else>{{item.desc}} </span>
        </td>
        <td><button @click="item.edit = !item.edit" class="btn btn-info">Edit The Item<i class="far fa-edit"></i></button>
          <button @click="removeItem(index)" class="btn btn-danger">Erase The Item<i class="far fa-trash-alt"></i></button></td>
      </tr>
    </table>
</div>


    </body>
</template>



<script scope>
  export default {
    data() {
    return {
      item: {name: "", Add: "", Dob: "", desc: "", edit: false},
      items: []
    }
  },
  methods:{
    addItem() {
      this.items.push({
        name:this.item.name, Add:this.item.Add, Dob:this.item.Dob, desc:this.item.desc, edit: false}
        );
      this.item = [];
    },
    removeItem(index){
      this.items.splice(index, 1)
    }
  }
  }
</script>






<style scoped>
.form-inline input {
  margin-right:8px;
}

nav {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color: #ef3636;
  }

li {
    float: left;
    border-right:1px solid #bbb;
  }

li:last-child {
    border-right: none;
  }

li a {
    display: block;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
  }

li a:hover:not(.active) {
    background-color: #111;
  }
</style>
<style scoped>
nav {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color:orange;
  }

li {
    float: left;
    border-right:1px solid #bbb;
  }

li:last-child {
    border-right: none;
  }

li a {
    display: block;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
  }

li a:hover:not(.active) {
    background-color: #111;
  }
</style>
