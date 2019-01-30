<template>
  <div class="fare">
    <h1 class="heading">List All Fares</h1>
    <ul>
      <li class="heading-title">
        <span class="fare--heading">From</span>
        <span class="fare--heading">To</span>
        <span class="fare--heading">Price</span>
      </li>
      <li v-for="(value,key,index) in data" :key="index" class="fare-towns">
        <span class="fare--town">{{value.departure}}</span>
        <span class="fare--town">{{value.destination}}</span>
        <span class="fare--town">D{{value.newfare}}</span>
      </li>
    </ul>
    <ul>
      <ul >
   
       
      </ul>
      <!-- <li>{{this.data.sheet[0].departure}}</li> -->
    </ul>
  </div>
</template>

<script>
import stuff from "../assets/data.json";
export default {
  data() {
    return {
      data: stuff
    };
  },

  methods: {
    filterItems: function(items){
      return items.fil
    }
  },

  mounted() {
    console.log(this.data.id);
  },
  computed:{
    filterByName(name){
      return this.data.filter((depart)=>{
        return depart == name  ;
      })
    }

    
  }
};
</script>

<style scoped>
.heading {
  color: #ffffff;
}
.heading-title {
  width: 40%;
  margin: 2rem auto;
}
.fare-towns {
  margin-top: 1rem;
  border: 2px solid #eee;
  background: #ffffff;
  width: 40%;
  margin: 2rem auto;
  border-radius: 5px;
  display: inline-block;
  padding: 1rem 0 1rem 0;
  font-weight: bold;
  display: block;
}

.fare--heading {
  padding-right: 2rem;
  font-size: 1.5rem;
  font-weight: bolder;

  color: #ffffff;
  margin-top: 2rem;
}
.fare--town {
  font-size: 1rem;
  padding: 2rem;
}
@media(min-width: 720px){
  

}
</style>