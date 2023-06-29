<script>
import AppSearch from './AppSearch.vue';
export default {
  components:{
    AppSearch

  }
}
</script>
<template lang="">
    <header>
      <div class="row">
        <div>
          <a href="http://localhost:5173" class="logo">
            <img src="public\boolflix_logo.png" alt="">
          </a>
        </div>
        <div class="search_bar">
          <AppSearch/>
        </div>
      </div>
    </header>
</template>
<style lang="scss" scoped>
  header{
    position: absolute;
    top: 0px;
    left: 0px;
    right: 0px;
    height: 70px;
    background-color: #141414;
    padding: 10px;

  }
  .row{
    display: flex;
    justify-content: space-between;
    height: 50px;
  }

  .logo{
    width: 200px;
    height: 50px;
    overflow: hidden;
  }

  .logo img{
    min-height: 100%;
    min-width: 100%;
    width: 200px;
    height: 50px;
    object-fit: cover;
    object-position: 3% 49%;
  }
  .search_bar{
    display: flex;
    align-items: center;
    justify-content: flex-end;
    height: 50px;
    padding-right: 40px;
  }
</style>