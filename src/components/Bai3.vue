<template>
    <div class="container mt-5">
        <div class="row">
            <!-- Form nhập thông tin -->
            <div class="col-md-6">
                <h3>Form Đăng Ký</h3>
                <form @submit.prevent="submitForm">
                    <div class="mb-3">
                        <label for="fullname" class="form-label">Họ tên:</label>
                        <input v-model="form.fullname" type="text" class="form-control" id="fullname" />
                    </div>
                    <div class="mb-3">
                        <label for="email" class="form-label">Email:</label>
                        <input v-model="form.email" type="email" class="form-control" id="email" />
                    </div>
                    <div class="mb-3">
                        <label for="password" class="form-label">Mật khẩu:</label>
                        <input v-model="form.password" type="password" class="form-control" id="password" />
                    </div>
                    <div class="mb-3">
                        <label for="birthday" class="form-label">Ngày sinh:</label>
                        <input v-model="form.birthday" type="date" class="form-control" id="birthday" />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Giới tính:</label>
                        <div class="form-check">
                            <input v-model="form.gender" class="form-check-input" type="radio" id="male" value="Nam" />
                            <label class="form-check-label" for="male">Nam</label>
                        </div>
                        <div class="form-check">
                            <input v-model="form.gender" class="form-check-input" type="radio" id="female" value="Nữ" />
                            <label class="form-check-label" for="female">Nữ</label>
                        </div>
                        <div class="form-check">
                            <input v-model="form.gender" class="form-check-input" type="radio" id="other"
                                value="Khác" />
                            <label class="form-check-label" for="other">Khác</label>
                        </div>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Ngôn ngữ:</label>
                        <div class="form-check form-check-inline">
                            <input v-model="form.languages" class="form-check-input" type="checkbox" id="vietnamese"
                                value="Tiếng Việt" />
                            <label class="form-check-label" for="vietnamese">Tiếng Việt</label>
                        </div>
                        <div class="form-check form-check-inline">
                            <input v-model="form.languages" class="form-check-input" type="checkbox" id="english"
                                value="Tiếng Anh" />
                            <label class="form-check-label" for="english">Tiếng Anh</label>
                        </div>
                        <div class="form-check form-check-inline">
                            <input v-model="form.languages" class="form-check-input" type="checkbox" id="japanese"
                                value="Tiếng Nhật" />
                            <label class="form-check-label" for="japanese">Tiếng Nhật</label>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary">Đăng ký</button>
                </form>
            </div>

            <div class="col-md-6">
                <h3>Thông tin đã đăng ký:</h3>
                <p><strong>Họ tên:</strong> {{ submittedData.fullname }}</p>
                <p><strong>Email:</strong> {{ submittedData.email }}</p>
                <p><strong>Ngày sinh:</strong> {{ submittedData.birthday }}</p>
                <p><strong>Giới tính:</strong> {{ submittedData.gender }}</p>
                <p><strong>Ngôn ngữ:</strong> {{ submittedData.languages.join(', ') }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            form: {
                fullname: "",
                email: "",
                password: "",
                birthday: "",
                gender: "",
                languages: [],
            },
            submittedData: {
                fullname: "",
                email: "",
                birthday: "",
                gender: "",
                languages: [],
            },
        };
    },
    methods: {
        submitForm() {
            // Sao chép dữ liệu từ form vào submittedData
            this.submittedData = { ...this.form, languages: [...this.form.languages] };
            // alert("Thông tin đã được lưu!");
        },
    },
};
</script>

<style scoped>
.container {
    max-width: 800px;
}
</style>