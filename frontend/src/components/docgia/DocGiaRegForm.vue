<template>
  <div class="container m-auto w-100">
      <form class="row g-3" @submit="register">
        <div class="col-md-3">
          <label for="maDocGia" class="form-label"></label>
          <input type="text" class="form-control" id="maDocGia" placeholder="Mã độc giả"
          v-model="docgiaLocal.maDocGia" required/>
        </div>
        <div class="col-md-6">
          <label for="password" class="form-label"></label>
          <input type="password" class="form-control" id="password" placeholder="Mật khẩu"
          v-model="docgiaLocal.password" required/>
        </div>
        <div class="col-md-8">
          <label for="hoLot" class="form-label"></label>
          <input type="text" class="form-control" id="hoLot" placeholder="Họ"
          v-model="docgiaLocal.hoLot" required/>
        </div>
        <div class="col-md-4">
          <label for="tenDocGia" class="form-label"></label>
          <input type="text" class="form-control" id="tenDocGia" placeholder="Tên"
          v-model="docgiaLocal.tenDocGia" required/>
        </div>
        <div class="col-12">
          <label for="diaChi" class="form-label"></label>
          <input type="text" class="form-control" id="diaChi" placeholder="Địa chỉ"
          v-model="docgiaLocal.diaChi" required/>
        </div>
        <div class="col-md-6">
          <label for="dienThoai" class="form-label"></label>
          <input type="text" class="form-control" id="dienThoai" placeholder="Số điện thoại"
          v-model="docgiaLocal.dienThoai" required/>
        </div>
        <div class="col-md-4">
          <label for="ngaySinh" class="form-label"></label>
          <input type="date" class="form-control" id="ngaySinh" placeholder="Ngày sinh"
          v-model="docgiaLocal.ngaySinh" required/>
        </div>
        <div class="col-md-2">
          <label for="gioiTinh" class="form-label"></label>
          <input type="text" class="form-control" id="gioiTinh" placeholder="Giới tính"
          v-model="docgiaLocal.gioiTinh" required/>
        </div>
        
        <div class="col-12">
          <button type="submit" class="btn btn-primary m-2">Đăng ký</button>
        </div>
      </form>
      <!-- <div class="mb-3 w-25  m-auto">
        <label for="hoLot" class="form-label">Họ lót</label>
        <input
          type="text"
          class="form-control"
          id="hoLot"
          v-model="docgiaLocal.hoLot"
        />
      </div>
      <div class="mb-3 w-25 m-auto" >
        <label for="tenDocGia" class="form-label">Tên</label>
        <input
          type="text"
          class="form-control"
          id="tenDocGia"
          v-model="docgiaLocal.tenDocGia"
        />
      </div>
      <div class="mb-3 w-25  m-auto">
        <label for="ngaySinh" class="form-label">Ngày sinh</label>
        <input
          type="date"
          class="form-control"
          id="ngaySinh"
          v-model="docgiaLocal.ngaySinh"
        />
      </div>
      <div class="mb-3 w-25  m-auto">
        <label for="gioiTinh" class="form-label">Giới tính</label>
        <input
          type="text"
          class="form-control"
          id="gioiTinh"
          v-model="docgiaLocal.gioiTinh"
        />
      </div>
      <div class="mb-3 w-25 m-auto">
        <label for="diaChi" class="form-label">Địa chỉ</label>
        <input
          type="text"
          class="form-control"
          id="diaChi"
          v-model="docgiaLocal.diaChi"
        />
      </div>
      <div class="mb-3 w-25 m-auto">
        <label for="dienThoai" class="form-label">Số điện thoại</label>
        <input
          type="text"
          class="form-control"
          id="dienThoai"
          v-model="docgiaLocal.dienThoai"
        />
      </div> -->
      <!-- <button type="submit" class="btn btn-primary m-2">Đăng ký</button> -->
  </div>
</template>
<script>
import { Form } from "vee-validate";
export default {
  components: {
    Form,
  },
  emits: ["submit:DocGia"],
  props: {
    docGia: {
      type: Object,
      default: () => ({
        maDocGia: "",
        password: "",
        hoLot: "",
        tenDocGia: "",
        ngaySinh: "",
        gioiTinh: "",
        diaChi: "",
        dienThoai: "",
      }),
    },
  },
  data() {
    return {
      docgiaLocal: { ...this.docGia },
    };
  },
  methods: {
    register(e) {
      e.preventDefault();
      this.$emit("submit:DocGia", this.docgiaLocal);
      
    },
  },
};
</script>
