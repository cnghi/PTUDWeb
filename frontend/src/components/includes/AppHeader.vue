<script>
import InputSearch from "@/components/includes/InputSearch.vue";
import DocGiaLog from "@/views/docgia/DocGiaLog.vue";
import NhanVienLog from "@/views/nhanvien/NhanVienLog.vue";
import { ref } from "vue";
// import { toast } from 'vue3-toastify';
// import 'vue3-toastify/dist/index.css';
export default {
  components: {
    InputSearch,
      NhanVienLog,
      DocGiaLog
  },
  data() {
    return {
      isLoggedIn: false,
      isLoggedInDocGia: false,
    };
  },
  created() {
    const docgia = JSON.parse(sessionStorage.getItem("docgia"));
    const nhanvien = JSON.parse(sessionStorage.getItem("nhanvien"));
    if (nhanvien) {
      this.isLoggedIn = true;
    }
    if(docgia){
      this.isLoggedInDocGia = true;
    }
  },
  methods: {
    async logout() {
      const nhanvien = sessionStorage.removeItem("nhanvien");
      const docgia = sessionStorage.removeItem("docgia");
      await this.$router.push({ name: "nhanvien.login" });
      if (nhanvien) {
        alert("Đăng xuất thành công");
        this.isLoggedIn = false;
      }
      if(docgia){
        alert("Đăng xuất thành công");
        this.isLoggedInDocGia = false;
      }
      window.location.reload();
    },
  },
  setup() {
    // if(sessionStorage.getItem("nhanvien") || sessionStorage.getItem("docgia")){
    //   toast.success('Chào mừng bạn đến với cửa hàng sách của TranStore',{
    //   timeout: 1000,
    //   });
    // }
    const nhanvien = ref(JSON.parse(sessionStorage.getItem("nhanvien")));
    const docgia = ref(JSON.parse(sessionStorage.getItem("docgia")));
    return { nhanvien,docgia };
  },
};
</script>
<style>
#nav{
  background-color: rgb(0, 0, 99);
}
</style>
<template>
   <div id="app">
    <main>
          <nav class="navbar navbar-expand-lg navbar-light" id="nav">
          <div class="container-fluid">
          <a v-if="isLoggedIn" href="/" class="navbar-brand text-white"
            >Quản lý {{ nhanvien.hoTenNhanVien }}</a
          >
          <a v-if="isLoggedInDocGia" href="#" class="navbar-brand text-white"
            > {{ docgia.tenDocGia }}</a
          >
          <button
              class="navbar-toggler text-white"
              type="button"
              data-toggle="collapse"
              data-target="#navbarText"
              aria-controls="navbarText"
              aria-expanded="false"
              aria-label="Toggle navigation"
            >
          <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarText">
        <ul class="navbar-nav me-auto">
          <li v-if="isLoggedIn" class="nav-item active text-white">
            <router-link :to="{ name: 'book' }" class="nav-link text-white">
              Sách
            </router-link>
          </li>
          <li v-if="isLoggedInDocGia" class="nav-item">
            <router-link :to="{ name: 'sachmuon' }" class="nav-link text-white">
              Thư viện sách
            </router-link>
          </li>
          <li v-if="isLoggedInDocGia" class="nav-item">
            <router-link :to="{ name: 'sachdamuon' }" class="nav-link text-white">
              Danh sách sách mượn
            </router-link>
          </li>
          <li v-if="isLoggedIn" class="nav-item">
            <router-link :to="{ name: 'showdocgia' }" class="nav-link text-white">
              Độc giả
            </router-link>
          </li>
          <li v-if="isLoggedIn" class="nav-item">
            <router-link :to="{ name: 'shownxb' }" class="nav-link text-white">
              Nhà xuất bản
            </router-link>
          </li>
           <li v-if="isLoggedIn" class="nav-item">
            <router-link :to="{ name: 'quanlysachmuon' }" class="nav-link text-white">
              Quản lý sách mượn
            </router-link>
          </li>
          <div class="row">
            <div class="dropdown col-6"  v-if="!isLoggedIn  && !isLoggedInDocGia">
                <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
                  Quản lý người dùng
                </button>
                <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
                  <li>
                    <router-link :to="{ name: 'nhanvien.register' }" class="nav-link dropdown-item">
                      Đăng ký quản lý
                    </router-link>
                  </li>
                  <li>
                    <router-link :to="{ name: 'nhanvien.login' }" class="nav-link dropdown-item">
                      Đăng nhập quản lý
                    </router-link>
                  </li>
                  <li class="nav-item">
                    <router-link :to="{ name: 'docgia.register' }" class="nav-link">
                      Đăng ký độc giả
                    </router-link>
                  </li>
                  <li class="nav-item">
                    <router-link :to="{ name: 'docgia.login' }" class="nav-link">
                      Đăng nhập độc giả
                    </router-link>
                  </li>
              </ul>
            </div>
          </div>
        </ul>
        <ul class="navbar-nav ms-auto">
          <li v-if="isLoggedIn || isLoggedInDocGia" class="nav-item">
            <router-link :to="{name:'nhanvien.login'}" @click="logout" class="nav-link text-white">
              Đăng xuất
            </router-link>
          </li>
          
         
        </ul>
      </div>
    </div>
  </nav>
</main>
</div>
</template>
