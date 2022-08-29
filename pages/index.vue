<template>
  <div>
 <div class="container">
        <div class="row">
            <div class="col-lg-12 text-center">
                <h1 class="page-title">Product List</h1>
            </div>
            <div class="col-lg-12 mt-5">
                <form action="#" method="post" enctype="multipart/form">
                    
                    <div class="row">
                        <div class="col-lg-8">
                            <div class="form-group">
                                <input class="form-control" name="name" type="text" placeholder="Enter Product" required>
                            </div> 
                            <div class="form-group">
                                <input class="form-control" name="price" type="text" placeholder="Enter Price" required>
                            </div> 
                        </div>
                        <div class="col-lg-4">
                        <button type="submit" class="btn btn-success">submit</button>
                    </div>
                </div>  
                
                </form>
               
            </div>
            <div class="col-lg-12 mt-5">
                <div>
                <table class="table table-success table-stripped">
                    <thead>
                        <tr>
                          <th scope="col">#</th>
                          <th scope="col">Name</th>
                          <th scope="col">Price</th>
                          <th scope="col">Image</th>
                          <th scope="col">Status</th>
                        
                        </tr>
                      </thead>
                      <tbody>
                      <tr v-for="task in tasks">
                        <td scope="row">{{ task.id }}</td>
                        <td>{{ task.name }}</td>
                        <td>{{ task.price }}</td>
                        <td>{{ task.image }}</td>
                        <td> <span v -if ="task.status == 0" class="badge bg-warning">Inactive</span>
                             <span class="badge bg-success">Active</span></td>
                      
                      </tr>
                         
                        
                      </tbody>
                    </table>

                </div>
            </div>
        </div>
    </div>

    <div class="modal fade" id="taskEdit" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1"
    aria-labelledby="taskEditLabel" aria-hidden="true">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title" id="taskEditLabel">Product Edit</h5>
              <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body" id="taskEditContent">
              
            </div>
            
          </div>
        </div>
      </div>



 </div>
</template>

<script>
export default {
  name: 'home',
  layout: 'dashboard',
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    getTasks() {
      this.$axios.get('api/tasks').then(response => {
        this.Tasks = response.data;
        console.log(this.tasks);
      });
    },
   
  },
  mounted() {
    this.getTasks();
  },


}
</script>

<style>
  .page-title {
        padding-top: 5vh;
        font-size: 5rem;
        color: #4bbf68;
  }
</style>
