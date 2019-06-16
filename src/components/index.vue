<template>

<div>
     <header id="portfolio">
    <a href="#"><img src="/w3images/avatar_g2.jpg" style="width:65px;" class="w3-circle w3-right w3-margin w3-hide-large w3-hover-opacity"></a>
    <span class="w3-button w3-hide-large w3-xxlarge w3-hover-text-grey" onclick="w3_open()"><i class="fa fa-bars"></i></span>
    <div class="w3-container">
    <h1><b>My Example Front-end developer</b></h1>
    <div class="w3-section w3-bottombar w3-padding-16">
      <span class="w3-margin-right"><b>FILTER: </b></span> 
      
      <input type="text" v-model="search" placeholder="Search Title"  style=" border-radius: 5px;">
    </div>
    </div>
  </header>
  
         <div class="row">
            <!-- <div id="app"></div> -->
            <div class="col-md-3"  v-for="item in filteredtitle">
            <img :src="item.url"  width="100%" style=" border-radius: 5px;">
            <div class="w3-container w3-white">
                
                <p><strong>Album ID :</strong>{{ item.albumId }}</p>
                <p><strong>Title :</strong>{{ item.title }}</p>
          
            </div>
            <br>
            </div>
        
  
        </div>
  
</div>
    
</template>

 

<script>
const API_URL = 'https://jsonplaceholder.typicode.com/albums/1/photos'


export default {
  name: 'index',
  data: function () {
    return {
      namedata: [] ,
      search:''
    }
  },
  computed:{
    filteredtitle: function(){
        return this.namedata.filter((item) => {
            return item.title.match(this.search);
           
        });
    }
   
  },

  methods: {
    loadDate: function () {
      this.$http.get(API_URL) 
        .then(response => {
          // console.log(response)
          this.namedata = response.body
        }, () => {
          this.namedata = []
        })
    }
  },
  created: function () {
    this.loadDate()
  }
}



</script>
