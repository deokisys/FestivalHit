<template>
<div>
    <div class="header-wrap">
      <div class="header-content">
        <div>
          <b-dropdown text="말머리" class="m-2" size="sm" variant="success">
            <b-dropdown-item @click="selCate('all')">전체</b-dropdown-item>
            <b-dropdown-item @click="selCate('hugi')">후기</b-dropdown-item>
            <b-dropdown-item @click="selCate('deal')">거래</b-dropdown-item>
          </b-dropdown>
        </div>
        <div>
          <b-button size="sm" class="m-2" variant="primary" @click="goWrite">
            게시글 등록
          </b-button>
        </div>
      </div>
    </div>
    <div class="carousel-wrap">
      <div class="carousel-window">
          <div class="carousel-content" v-if="boardList.length">
            <template v-for="(ele,i) in boardList">
              <div :key="i" @click="goArticle(ele.boardId)">
                <card class="card" style="width: 300px;"  >
                  <img slot="image" class="card-img-top" :src="showImage(ele.boardId)" alt="Card image cap">
                  <p class="card-text">{{ele.title}}</p>
                </card>
              </div>
            </template>
          </div>
          <div class="carousel-content" v-else>
            <card class="card">
              <img slot="image" class="card-img-top" src="data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%22320%22%20height%3D%22180%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20viewBox%3D%220%200%20320%20180%22%20preserveAspectRatio%3D%22none%22%3E%3Cdefs%3E%3Cstyle%20type%3D%22text%2Fcss%22%3E%23holder_1664f761b63%20text%20%7B%20fill%3Argba(255%2C255%2C255%2C.75)%3Bfont-weight%3Anormal%3Bfont-family%3AHelvetica%2C%20monospace%3Bfont-size%3A16pt%20%7D%20%3C%2Fstyle%3E%3C%2Fdefs%3E%3Cg%20id%3D%22holder_1664f761b63%22%3E%3Crect%20width%3D%22320%22%20height%3D%22180%22%20fill%3D%22%23777%22%3E%3C%2Frect%3E%3Cg%3E%3Ctext%20x%3D%22110.203125%22%20y%3D%2297.35%22%3EImage%20cap%3C%2Ftext%3E%3C%2Fg%3E%3C%2Fg%3E%3C%2Fsvg%3E" alt="Card image cap">
              <p class="card-text">게시판에 어서오세요!</p>
            </card>
          </div>
      </div>
    </div>
    <div class="page-wrap">
    <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      :limit="limit"
      size="sm"
      @page-click="pageClick"
    ></b-pagination>
    </div> 
</div>
</template>


<script>
import {articleList,getImage} from "@/util/boardApi.js";

export default {
  data(){
    return{
      festivalId:"",
      currentPage:1,
      rows:0,//전체 게시글 수
      perPage:4,//하나의 페이지당 보여질 게시글
      limit:10,//네비게이션에 보여지는 페이지 갯수
      boardList:[],
      cate:"all"
    }
  },
  created(){
    this.festivalId = this.$route.params.festivalId;//축제 번호
    articleList(
      {
        festivalId:this.festivalId,
        pgno:this.currentPage,
        cate:this.cate
      },
      ({data})=>{
        this.rows = data.articleCnt;
        this.boardList = data.boardList;
      },
      ()=>{
        alert("잘못된 접근입니다.")
      })
  },
  components:{
  },
  methods:{
    pageClick(_,page){
      this.currentPage = page;
      articleList(
        {
          festivalId:this.festivalId,
          pgno:this.currentPage,
          cate:this.cate
        },
        ({data})=>{
          this.rows = data.articleCnt;
          this.boardList = data.boardList;
        },
        ()=>{
          alert("잘못된 접근입니다.")
        })
    },
    selCate(cate){//말머리 변경
      this.cate = cate;
      articleList(
      {
        festivalId:this.festivalId,
        pgno:1,
        cate:this.cate
      },
      ({data})=>{
        this.rows = data.articleCnt;
        this.boardList = data.boardList;
        this.currentPage=1;//1페이지로 초기화
      },
      ()=>{
        alert("잘못된 접근입니다.")
      })
    },
    goWrite(){
      this.$router.push(`/boardwrite/${this.festivalId}`)
    },
    showImage(boardId){
      let tmp = getImage(boardId)
      return tmp
    },
    goArticle(boardId){
      this.$router.push(`/boardView/${this.festivalId}/${boardId}`);
    }
  }
}

</script>


<style>
.carousel-wrap{
  width:100%;
  display: flex;
  justify-content: center;
  /* background-color: red; */
}

.carousel-window{
  display: flex;
  flex-wrap: nowrap;
  overflow-y: auto;
  width:1200px;
}
.carousel-content{
  display: flex;
}

.page-wrap{
  display: flex;
  justify-content: center;
  width: 100%;
}

.header-wrap{
  width:100%;
  display: flex;
  justify-content: center;
}
.header-content{
  width:1200px;
  display: flex;
  justify-content: space-between;
}
.card-img-top{
  height:300px;
  object-fit: cover;
}
</style>