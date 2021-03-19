<template>
  <div>
    <section id = "navbar">
      <div class = "nav-list">
          <ul class = "navbar-unlist">
              <li class = "nav-li current"><router-link to = "/">Home</router-link></li>
              <li class = "nav-li"> <router-link to = "/CategorizeScripture">Categorize</router-link></li>
              <li class = "nav-li"><router-link to = "/AddScripture">Add Scripture List</router-link></li>
          </ul>
      </div>   
    </section>    
    <div id="totalListNum" class="marginPlus">
      <span>Total number of scriptures in list: </span><span class="spanRed">{{this.$root.$data.totalNum}}</span>
    </div>
    <div id="btnWrap">
      <button class="expendBtn" v-if="!this.$root.$data.isExpend" @click="expendScriptureList()">Expend List</button>
      <button class="shrinkBtn" v-if="this.$root.$data.isExpend" @click="shirnkScriptureList()">Shrink List</button>
    </div>
    <div v-if="this.$root.$data.isExpend">  
      <ScriptureList :scriptures="scriptures" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ScriptureList from "../components/ScriptureList.vue"
export default {
  name: 'Home',
  components: {
    ScriptureList
  },

  methods: {
    expendScriptureList(){
      this.$root.$data.isExpend = true;
    },

    shirnkScriptureList(){
      this.$root.$data.isExpend = false;
    }
  },

  computed: {
    scriptures(){
      return this.$root.$data.scriptures
    }
  }
}
</script>

<style>
  .marginPlus{
    margin-top:100px;
  }

  #btnWrap {
    display:flex;
    justify-content:center;
  }

  #btnWrap .expendBtn{
    padding:5px 5px;
    color: white;
    background: #4C8FFB;
    border: 1px #3079ED solid;
    box-shadow: inset 0 1px 0 #80B0FB;
    font-size:24px;
    margin-top:50px;
    margin-bottom:50px;
  }

  #btnWrap .shrinkBtn{
    padding:5px 5px;
    color: white;
    background: -webkit-linear-gradient(top, #DD4B39, #D14836); 
    border: 1px solid #DD4B39;
    box-shadow: inset 0 1px 0 #80B0FB;
    text-shadow: 0 1px 0 #C04131;
    font-size:24px;
    margin-top:50px;
    margin-bottom:50px;
  }

</style>

