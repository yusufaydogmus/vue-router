<template>
    <div class="card  p-2">
      <div class="d-flex justify-content-end ">
        <button class="btn btn-primary btn-sm" @click="$router.push({name:'NewBookmark'})">+ Yeni Ekle</button>
      </div>
      <div class="card-body d-inline-block">
        <table class="table table-striped table-hover">
          <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">Başlık</th>
              <th scope="col">URL</th>
              <th scope="col">Sil</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(bookmark,index) in bookmarkList" :key="bookmark.id">
              <th scope="row">{{ index+1}}</th>
              <td>{{bookmark.title}}</td>
              <td>
              <a :href="bookmark.url" target="_blank" >{{ bookmark.url }} </a>
              </td>
              <td>
                <button class="btn btn-sm btn-danger" @click="deleteBookmark(bookmark)">Sil</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>





</template>
<script>
export default{
  data(){
return{
  bookmarkList:[],
}
  },
    created(){
      this.$appAxios.get("/bookmarks").then(bookmarks_list_response=>{
      this.bookmarkList=bookmarks_list_response.data || [];
      console.log(bookmarks_list_response);
      });
    },
    methods: {
    deleteBookmark(bookmark){
     //console.log("bookmark:>> ",bookmark);
      this.$appAxios.delete(`/bookmarks/${bookmark.id}`).then(delete_response=>{
        console.log(delete_response);
        if(delete_response.status==200){
          this.bookmarkList=this.bookmarkList.filter(b=>b.id !=bookmark.id )
        }
      });
    }
    }
  };
  
  
</script>
