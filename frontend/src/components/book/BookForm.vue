<template>
  <Form @submit="submitBook">
    <div class="form-group">
      <label for="maSach"></label>
      <Field
        name="maSach"
        type="text"
        class="form-control text-center"
        v-model="bookLocal.maSach"
        placeholder="Mã sách"
      />
    </div>
    <div class="form-group">
      <label for="tenSach"></label>
      <Field
        name="tenSach"
        type="text"
        class="form-control text-center"
        v-model="bookLocal.tenSach"
        placeholder="Tên sách"
      />
    </div>
    <div class="form-group">
      <label for="tacGia"></label>
      <Field
        name="tacGia"
        type="text"
        class="form-control text-center"
        v-model="bookLocal.tacGia"
        placeholder="Tác giả"
      />
    </div>
    <div class="form-group">
      <label for="namXuatBan"></label>
      <Field
        name="namXuatBan"
        type="text"
        class="form-control text-center"
        v-model="bookLocal.namXuatBan"
        placeholder="Năm xuất bản"
      />
    </div>
    <div class="form-group">
      <label for="maNXB"></label>
      <Field
        name="maNXB"
        type="text"
        class="form-control text-center"
        v-model="bookLocal.maNXB"
        placeholder="Nhà xuất bản"
      />
    </div>
    <div class="form-group">
      <label for="soQuyen"></label>
      <Field
        name="soQuyen"
        type="text"
        class="form-control text-center"
        v-model="bookLocal.soQuyen"
        placeholder="Số quyển"
      />
    </div>
    <div class="form-group">
      <label for="donGia"></label>
      <Field
        name="donGia"
        type="text"
        class="form-control text-center"
        v-model="bookLocal.donGia"
        placeholder="Giá"
      />
    </div>
    <div class="form-group mt-2">
      <button class="btn btn-primary mx-2"><i class="fas fa-save"></i> Lưu</button>
      <button
        v-if="bookLocal._id"
        type="button"
        class="ml-2 btn btn-danger"
        @click="deleteBook"
      >
        <i class="fas fa-trash"></i>
        Xóa
      </button>
    </div>
  </Form>
</template>

<script>
import { Form, Field,  } from "vee-validate";

export default {
  components: {
    Form,
    Field
  },
  emits: ["submit:Sach", "delete:Sach"],
  props: {
    Sach: { type: Object, required: true },
  },
  data() {
    return {
      bookLocal: this.Sach,
    };
  },
  methods: {
    submitBook() {
      this.$emit("submit:Sach", this.bookLocal);
    },
    deleteBook() {
      this.$emit("delete:Sach", this.bookLocal.id);
    },
  },
};
</script>
<style scoped>
@import "@/assets/form.css";
</style>
