
<script>
import axios from 'axios'


export default {
  name: "HelloWorld",
  data() {
    return {
  contents: null
    }
  },
  mounted () {
    axios
      .get('http://localhost:5173/api/v1/search?apikey=Gx5geY9njS2SfS3PaKsrXX0KHYWxwBkB')
      // .get('https://wallhaven.cc/api/v1/search?apikey=Gx5geY9njS2SfS3PaKsrXX0KHYWxwBkB')
      .then(response => (console.log(response)))
    
  }
};

// console.log("test");
//        const apiCall = `https://wallhaven.cc/api/v1/search?apikey=Gx5geY9njS2SfS3PaKsrXX0KHYWxwBkB`
  //     //  const response = await fetch(apiCall)
//   const myHeaders = new Headers();
//   console.log(myHeaders)
//   const myInit = {
//   method: 'GET',
//   headers: myHeaders,
//   mode: 'no-cors',
//   cache: 'default'
// };




// fetch(apiCall)
      // .then(response => (console.log( response)))
      // .catch(err => {console.log(err)})
</script>

<template>
  <div>
 <div><h1>Search for Wallpapers</h1></div>
    <div class="form"> <form action="" @submit.prevent="search">
       <label for="query">Search:</label>
       <input type="text" v-model="query" id="query" name="query">
       <br>
       <label for="sort">Sort by:</label>
       <select  v-model="sort" id="sort" name="sort">
         <option value="relevance">Relevance</option>
         <option value="date_added">Date</option>
         <option value="downloads">Downloads</option>
       </select>
       <br>
       <label for="order">Order:</label>
       <select v-model="order" id="order" name="order">
         <option value="asc">Ascending</option>
         <option value="desc">Descending</option>
       </select>
       <br>
       <label for="resolution">Resolution:</label>
       <select v-model="resolution" id="resolution" name="resolution">
         <option value="all">All</option>
         <option value="1920x1080">1920x1080</option>
         <option value="2560x1440">2560x1440</option>
         <option value="3840x2160">3840x2160</option>
       </select>
       <br>
       <input type="submit" value="Search">
     </form></div> </div>
     <!-- <div id="results">
       <template v-for="wallpaper in wallpapers">
         <div class="thumbnail" @click="showModal(wallpaper)">
           <img :src="wallpaper.thumb" alt="">
         </div>
       </template>
     </div> -->
     <modal v-if="show" @close="show = false">
       <img :src="selectedWallpaper.path" alt="">
     </modal>
</template>

<style>    
body {
  font-family: Arial, sans-serif;
  background-color: #DFCFBE;
}

#app{  
  display: flex;
  justify-content: center;
  align-items: center;
}

h1 {
  text-align:center;
  color:#fff
}

form {
  display: flex;
  flex-direction: column;
  width: 50%;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  border-color:#000;
}

label {
  font-weight: bold;
  margin-bottom: 10px;
  text-align:left;
  color: #fff;
}

input[type="text"], select {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-bottom: 20px;
  font-size: 14px;
}

.form{
  width:800px;
}

input[type="submit"] {
  width: 100%;
  background-color: #7c7bbc;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
} 

input[type="submit"]:hover {
  background-color: #64647d;
}

select {
  width: 200px;
  height: 37px;
  margin-bottom: 16px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 8px;
}

#results {
  display: flex;
  flex-wrap: wrap;
  margin: 16px;
}

.thumbnail {
  width: 200px;
  height: 120px;
  margin: 8px;
  border: 1px solid #ccc;
  cursor: pointer;
}

.thumbnail img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

#results {
  margin: 20px 0;
}

.result {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.result img {
  width: 200px;
  height: 120px;
  object-fit: cover;
  border-radius: 5px;
  margin-right: 20px;
}

.result .info {
  display: flex;
  flex-direction: column;
}

.result .title {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 5px;
}

.result .details {
  font-size: 14px;
  color: #666;
}
</style>
