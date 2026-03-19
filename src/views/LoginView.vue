<template>
  <div class="login-page">
    <BrandPanel />
    <div class="right-panel">
      <LoginForm />
    </div>
  </div>
</template>

<script>
import BrandPanel from '../components/BrandPanel.vue';
import LoginForm from '../components/LoginForm.vue';

export default {
  name: 'LoginView',
  components: { BrandPanel, LoginForm },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=DM+Sans:wght@400;500;600&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.login-page {
  display: flex;
  min-height: 100vh;
  font-family: 'DM Sans', sans-serif;
  background: #f0f0f0;
}

.right-panel {
  width: 58%;
  background: #ffffff;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 48px;
}

@media (max-width: 768px) {
  .login-page {
    flex-direction: column;
  }
  .right-panel {
    width: 100%;
    padding: 32px 24px;
  }
}
</style>