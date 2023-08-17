<template>
  <div class="d-flex justify-content-center align-items-center" >
    <div class="form-area card border p-2" style="width: 400px;">
      <div class="my-4">
        <label for="title" class="form-label">Başlık</label>
        <input type="text" v-model="userData.title" class="form-control" id="title" placeholder="Başlık">
      </div>
      <div class="my-4">
        <label for="url" class="form-label">URL</label>
        <input type="text"  v-model="userData.url" class="form-control" id="url" placeholder="https://...">
      </div>
      <div class="my-4">
        <label for="description" class="form-label">Açıklama</label>
        <textarea class="form-control" v-model="userData.description" id="description" placeholder="Açıklama" rows="3"></textarea>
      </div>
      <div class="d-flex justify-content-end align-items-center ">
        <button class="btn btn-sm btn-secondary m-2" @click="$router.push({name:'HomePage'})">İptal</button> <!-- $router.go(-1) bir önceki yönlendirmeye gider -->
        <button class="btn btn-sm btn-primary " @click="onSave">Kaydet</button>
      </div>
    </div>
  </div>
</template>
<script>
export default{
  data(){
    return{ //form elemanları var optionsAPI kullanırken fieldlardaki bilgilieri yazarım
      userData:{
        title:null,
        url:null,
        description:null //endpoint bizden bu bilgilerin tamamını istiyor olacak 
      }
    };
  },
  methods: {
    onSave(){
      console.log(this.userData);
      this.$appAxios.post("/bookmarks",this.userData).then(save_response=>{
        console.log("save_response",save_response);
        this.resetData();
        this.$router.push("/")
      }); 
    },
    resetData(){
    Object.keys(this.userData).forEach(key=>(this.userData[key]=null));
  }  
  }
  
};

</script>
