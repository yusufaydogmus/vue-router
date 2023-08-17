<template>
        <div class="card">
  <img src="../assets/logo.png" alt="Avatar" style="width:30%">
  <div class="container">
    <h4><b>{{ userName }}</b></h4>
    <p>Architect & Engineer</p>
  </div>
</div>
</template>

<script>
export default{
  name:"MyCard",
  data(){
    return{
      userName:"yusuf aydoğmuş"
    }
  },
  methods: {
    getName(name){
      this.userName=name;
    }
    
  },
}

</script>