<template>
    <div class="container m-auto w-100">
        <form @submit="register">
            <section class="vh-100 gradient-custom">
                <div class="container py-5 h-100">
                    <div class="row justify-content-center align-items-center h-100">
                    <div class="col-12 w-100 col-lg-9 col-xl-7">
                        <div class="card shadow-2-strong card-registration" style="border-radius: 15px;">
                        <div class="card-body p-4 p-md-5">
                                <div class="row">
                                    <div class="col-md-6">

                                    <select v-model="nhanVienLocal.thuThu" class="select form-control-lg">
                                        <option value="">Thủ thư</option>
                                    </select>
                                    </div>
                                    <div class="col-md-6 mb-4">

                                    <div class="form-outline">
                                        <input type="text" id="maNhanVien" class="form-control form-control-lg" placeholder="Mã nhân viên" v-model="nhanVienLocal.maNhanVien"/>
                                        <label class="form-label" for="maNhanVien"></label>
                                    </div>

                                    </div>
                                </div>

                            <div class="row">
                                <div class="col-md-8 mb-4">

                                <div class="form-outline">
                                    <input type="text" id="hoTenNhanVien" class="form-control form-control-lg" placeholder="Username" v-model="nhanVienLocal.hoTenNhanVien"/>
                                    <label class="form-label" for="hoTenNhanVien"></label>
                                </div>

                                </div>
                                <div class="col-md-4 mb-4">

                                <div class="form-outline">
                                    <input type="password" id="password" class="form-control form-control-lg" placeholder="Mật khẩu" v-model="nhanVienLocal.password"/>
                                    <label class="form-label" for="password"></label>
                                </div>

                                </div>
                            </div>

                            <div class="row">
                                <div class="col-md-6 mb-4 pb-2">

                                <div class="form-outline">
                                    <input type="text" id="diaChi" class="form-control form-control-lg" placeholder="Địa chỉ" v-model="nhanVienLocal.diaChi"/>
                                    <label class="form-label" for="diaChi"></label>
                                </div>

                                </div>
                                <div class="col-md-6 mb-4 pb-2">

                                <div class="form-outline">
                                    <input type="text" class="form-control form-control-lg" id="dienThoai" placeholder="Số điện thoại" v-model="nhanVienLocal.dienThoai" />
                                    <label class="form-label" for="dienThoai"></label>
                                </div>

                                </div>
                            </div>
                            <div class="mt-4 pt-2">
                                <input class="btn btn-primary btn-lg" type="submit" value="Đăng ký" />
                            </div>
                            
                        </div>
                        </div>
                    </div>
                    </div>
                </div>
            </section>
        </form>
    </div>
        <!-- <div class="mb-3 w-25 m-auto">
            <label for="maNhanVien" class="form-label">Mã nhân viên</label>
            <input type="text" class="form-control" id="maNhanVien" placeholder="Mã nhân viên" v-model="nhanVienLocal.maNhanVien" />
        </div>
        <div class="mb-3  m-auto w-25">
            <label for="tenNhanVien" class="form-label">Tên nhân viên</label>
            <input type="text" class="form-control" id="tenNhanVien" placeholder="Tên nhân viên" v-model="nhanVienLocal.hoTenNhanVien" />
        </div>
        <div class="mb-3 w-25 m-auto">
            <label for="chucVu" class="form-label">Chức vụ</label>
            <input type="text" class="form-control" id="chucVu" placeholder="Chức vụ" v-model="nhanVienLocal.chucVu" />
        </div>
        <div class="mb-3 w-25 m-auto">
            <label for="password" class="form-label">Mật khẩu</label>
            <input type="password" class="form-control" id="password" placeholder="Mật khẩu" v-model="nhanVienLocal.password" />
        </div>
        <div class="mb-3 w-25 m-auto">
            <label for="diaChi" class="form-label">Địa chỉ</label>
            <input type="text" class="form-control" id="diaChi" placeholder="Địa chỉ" v-model="nhanVienLocal.diaChi" />
        </div>
        <div class="mb-3 w-25 m-auto">
            <label for="dienThoai" class="form-label">Số điện thoại</label>
            <input type="text" class="form-control" id="dienThoai" placeholder="Số điện thoại" v-model="nhanVienLocal.dienThoai" />
        </div> -->
        <!-- <button type="submit" class="btn btn-primary m-2 btn-block">Đăng ký</button> -->

</template>
<script>
import { Form } from 'vee-validate';
export default {
    components: {
        Form
    },
    emits: ['submit:NhanVien'],
    props: {
        nhanVien: {
            type: Object,
            default: () => ({
                maNhanVien: '',
                hoTenNhanVien: '',
                chucVu: '',
                password: '',
                diaChi: '',
                dienThoai: ''
            })
        }
    },
    data() {
        return {
            nhanVienLocal: {...this.nhanVien},
        }
    },
    methods: {
        register(e) {
            e.preventDefault();
            this.$emit('submit:NhanVien', this.nhanVienLocal)
        }
    }
}   
</script>