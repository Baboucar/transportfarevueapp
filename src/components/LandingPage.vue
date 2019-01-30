<template>
  <div class="container">
    <header class="header">
      <img alt="Vue logo" src="../assets/logo.png">
    </header>
    <h2 class="primary-heading">Transport Fare</h2>
    <p class="sub-heading">Know the transport fare of 1000's of places in The Gambia !</p>

    <form action class="flex-form">
      <div>
        <input v-model="searchText" type="text" name id placeholder="Search for a town">
      </div>
    </form>
    <div class="fare">
      <!-- <ul v-show="search.length > 0">
          <li class="heading-title">
            <span class="fare--heading">From</span>
            <span class="fare--heading">To</span>
            <span class="fare--heading">Price</span>
          </li>
      </ul>-->
      <ul class=" list-towns">
        <li v-for="value in search" :key="value.id" class="container fare-towns">
          <span class="from fare--town">{{value.departure.toUpperCase()}}</span>
          <span class="fare--town">{{value.destination.toUpperCase()}}</span>
          <span class="fare--town">{{value.price}}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import stuff from "../assets/data.json";
import axios from "axios";
export default {
  data() {
    return {
      data: stuff,
      list: [],
      searchText: ""
    };
  },

  computed: {
     
    search: function() {
       const re = new RegExp(this.searchText.trim(),'gi');
  return  this.list.filter(d => {
        // return  d.departure.indexOf(this.searchText) >=0;
        return (
        //   d.departure == this.searchText.toLowerCase().trim() ||
        //   d.destination == this.searchText.toLowerCase().trim()
        //  d.departure.includes(this.searchText) || d.destination.includes(this.searchText)
        //   || d.price.includes(this.searchText)
          d.departure.match(re) || d.destination.match(re) || d.price.match(re)
         );
      });
    }
  },
  methods: {
    fetchData: function() {
      axios
        .get("https://limitless-earth-82453.herokuapp.com/api/fares")
        .then(response => {
          this.list = response.data;
          console.log(this.list);
        })
        .catch(error => console.log(error));
    }
  },

  created: function() {
    this.fetchData();
  }
};
</script>

<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
* {
  margin: 0;
  padding: 0;
}
::-webkit-scrollbar { 
    display: none; 
}
.container {
  width: 90%;
  margin: 0 auto;
  color: #ffffff;
}

.primary-heading {
  font-size: 2em;
}

.sub-heading {
  font-weight: bold;
  margin-top: 1rem;
}

input {
  height: 50px;
  width: 100%;
  margin-top: 2rem;
  border-radius: 5px;
  border: none;
  background: #ffffff;
  box-shadow: 0 0 0 1px #c4cdd5;

  font-size: 1rem;
}
/* ::placeholder,option{
    padding-left: 1rem;
    font-size: 1rem
} */
.banner {
  width: 50%;
  margin-top: 3rem;
}
.from {
  text-align: left;
}

.list-towns {
 position: fixed;
    overflow-y: scroll;
    width: 90%;
    max-height: 100%;
    scroll-behavior: smooth;
    background: #5661a7;

}

.fare-towns {
  margin-top: 1rem;
  background: #ffffff;
  color: #000;
  margin-top: 1rem;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  padding: 1rem 0 1rem 0;
  font-weight: bold;
  width: 100%;
}
.fare--town {
  padding-right: 1rem;

  display: inline-block;
}

@media (min-width: 64rem) {
  .flex-form {
    width: 70%;
    margin: 0 auto;
  }
  .primary-heading {
    font-size: 3.75em;
  }
  .sub-heading {
    font-size: 2.25em;
    margin-top: 1rem;
  }
  .fare--town {
    font-size: 1rem;
  }
  .fare-towns {
    margin-top: 1rem;

    background: #ffffff;
    color: #000;
    width: 50%;
    margin: 2rem auto;
    border-radius: 5px;
    display: inline-block;
    padding: 1rem 0 1rem 0;
    font-weight: bold;
    display: block;
  }

  ::placeholder {
    padding: 1rem;
    font-size: 2rem;
    text-align: center;
  }
  input {
    font-size: 2rem;
    height: 70px;
  }
}
.heading {
  color: #ffffff;
}
.heading-title {
  margin: 2rem auto;

  list-style-type: none;
}

.fare--heading {
  padding-right: 2rem;
  font-size: 1.5rem;
  font-weight: bolder;

  color: #ffffff;
  margin-top: 2rem;
}
</style>