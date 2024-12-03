<template>
    <div class="container">
        <!-- Nếu người dùng chưa đăng nhập, hiển thị form đăng nhập -->

        <Login v-if="!isLoggedIn" @LoggedIn="handleLoginSuccess" />

        <!-- Nếu người dùng đã đăng nhập, hiển thị component bình luận -->
        <Comment v-else :username="loggedInUser" />
    </div>
</template>

<script setup>
    import { ref } from 'vue';

    import Login from './Login.vue';
    import Comment from './Comment.vue';

    // Quản lý trạng thái đăng nhập và tên người dùng đã đăng nhập
    const isLoggedIn = ref(false);
    const loggedInUser = ref('');

    // Xử lý khi người dùng đăng nhập thành công
    function handleLoginSuccess(username) {
        loggedInUser.value = username;
        isLoggedIn.value = true;
    }
</script>