<template>
<div class = "wrapper">   
    <div class = "scripture">
        <div class = scripture v-for="scripture in scriptures" :key="scripture.id">
            <div class ="scriptureInfo">
                <div class="scriprueContainer">
                  <div class="scriptureTitleSection">
                    <h1>{{scripture.book}} {{scripture.chapter}} : {{scripture.verse}}</h1>
                    <h3>({{scripture.topic}})</h3>
                  </div>
                  <div class="scriptureBodySection">
                    <p>{{scripture.content}}</p>
                    <button @click="removeFromList(scripture.id)" class="removeBtn">Remove</button>
                  </div>
                </div>
                <hr>
            </div>    
        </div>
    </div>
</div>
</template>

<script>
export default {
  name: 'ScriptureList',
  props: {
    scriptures: Array,
  },

  methods: {
    removeFromList(id) {
      this.$root.$data.totalNum--;
      this.$root.$data.scriptures = this.$root.$data.scriptures.filter(scripture => scripture.id !== id);
    }
  }

}
</script>

<style>
  .scriptureInfo{
    display:flex;
    flex-direction:column;
    justify-content: space-between;
    width:90%;
    margin:0 auto;
    text-align:center;
  }

  .scriptureInfo button{
    width:70px;
    padding:5px 0;
    margin:0 auto;
   }

   .scriptureInfo h1,
   .scriptureInfo h3,
   .scriptureInfo p,
   .scriptureInfo button {
     margin-bottom: 15px;
   }

   .scriptureInfo .removeBtn{
    padding:8px 8px;
    color: white;
    background:#ff4a20; 
    border: 1px solid #DD4B39;
    font-size:14px;
    border-radius:10px;
   }

   .scriptureInfo p{
    font-family: sans-serif;
    max-width:800px;
    margin:0 auto;
    margin-bottom:20px;
   }

    @media screen and (min-width:1200px){
      
      .scriptureInfo .scriprueContainer {
        width:100%;
        display:flex;
        justify-content:flex-start;
        margin:0 auto;
        padding-top:20px;
      }
      .scriptureInfo .scriprueContainer p{
        margin-left:20px;
        margin-top:10px;
      }

      .scriptureInfo h1{
        font-size: 22px;
      }

      .scriptureInfo .scriptureBodySection{
        display:flex;
      }

      .scriptureInfo .scriptureBodySection button{
        height:40px;
        margin-top:30px;
        margin-left:10px;
      }

    }

</style>