<template>
  <div>
    <h2 class="bg-info text-uppercase text-white text-center">List Of BlockBuster Movies</h2>
    <div class="card-header">
      <h5>Enter the Details of New Movie</h5>
      </div>
      <div class="form-group">
        <label>Movie Name :</label>
        <input type="text" v-model="mov.name" class="form-control" placeholder="Enter Movie Name" />
      </div>

      <div class="form-group">
        <label>Category: </label>
        <input type="text" v-model="mov.category" class="form-control" placeholder="Enter Category" />
      </div>

      <div style="margin-top:5px">
        <label>Release Year:</label>  
        <select v-model="mov.year" >
          <option value="2020">2020</option>
          <option value="2019">2019</option>
          <option value="2018">2018</option>
          <option value="2017">2017</option>
          <option value="2016">2016</option>
          <option value="2015">2015</option>
        </select>
      </div>
      <button @click="addNewMovie()" class="btn btn-primary">Add New Movie</button>&nbsp;&nbsp;&nbsp;
      <button @click="resetMovie()" class="btn btn-primary">Reset</button>
    

    <div v-for="(e,index) in listOfMovies" :key="e.id">
      <h3>Details of Movies #{{index+1}}</h3>
      <p>ID : {{e.id}}</p>
      <p>Name : {{e.name}}</p>
      <p>Category : {{e.category}}</p>
      <p>Release Year : {{e.year}}</p>
      <button>Update Details</button>&nbsp;&nbsp;
      <button @click="deleteMovie(index)">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      mov: { year: 2020 },
      movie: { id: 1, name: "Bahubaali", category: "Historic", year: "2018" },
      listOfMovies: [
        { id: 2, name: "Bhoot", category: "Horror", year: "2020" },
        { id: 3, name: "Toilet", category: "Motivational", year: "2019" },
        { id: 4, name: "DDLJ", category: "Romantic", year: "1999" },
        { id: 5, name: "Pink", category: "Suspense", year: "2017" },
        { id: 6, name: "Jolly LLB", category: "Drama", year: "2016" }
      ]
    };
  },

  methods: {
    addNewMovie() {
      var d = new Date();
      this.mov.id = d.getMilliseconds();
      console.log(this.mov);
      this.listOfMovies.push(this.mov);
    },
    deleteMovie(index) {
      this.listOfMovies.splice(index, 1);
    },
    resetMovie() {
      this.mov = {};
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
