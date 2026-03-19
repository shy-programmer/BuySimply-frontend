<template>
  <div class="form-container">

    <div class="mobile-logo">
        <img src= "../assets/brand_logo.png" alt="logo" class="mobile-logo-img" />
    </div>
    <h1 class="welcome-title">Welcome Back</h1>
    <p class="welcome-subtitle">Enter your email address and password to access your account.</p>

    <form @submit.prevent="handleLogin" class="login-form">

      <InputField
        label="Email Address"
        v-model="form.email"
        placeholder="Enter your email"
        :error="errors.email"
      />

      <InputField
        label="Password"
        v-model="form.password"
        placeholder="Enter your password"
        :isPassword="true"
        :showPassword="showPassword"
        :error="errors.password"
        @toggle="showPassword = !showPassword"
      />

      <div class="form-options">
        <label class="remember-me">
          <input type="checkbox" v-model="form.remember" class="checkbox" />
          <span class="checkbox-label">Remember me</span>
        </label>
        <a href="#" class="forgot-password">Forgot Password?</a>
      </div>

      <div v-if="loginError" class="login-error">
        {{ loginError }}
      </div>

      <button type="submit" class="sign-in-btn" :disabled="loading">
        <span v-if="loading" class="loader"></span>
        <span v-else>Sign in</span>
      </button>

      <p class="signup-text">
        Don't have an account?
        <a href="#" class="signup-link">Sign up</a>
      </p>

    </form>
  </div>
</template>

<script>
import InputField from './InputField.vue';

export default {
  name: 'LoginForm',
  components: { InputField },
  data() {
    return {
      form: {
        email: '',
        password: '',
        remember: false,
      },
      showPassword: false,
      loading: false,
      loginError: '',
      errors: {
        email: '',
        password: '',
      },
    };
  },
  methods: {
    validate() {
      this.errors = { email: '', password: '' };
      let valid = true;

      if (!this.form.email) {
        this.errors.email = 'Email is required';
        valid = false;
      } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.form.email)) {
        this.errors.email = 'Enter a valid email address';
        valid = false;
      }

      if (!this.form.password) {
        this.errors.password = 'Password is required';
        valid = false;
      }

      return valid;
    },

    async handleLogin() {
      if (!this.validate()) return;

      this.loading = true;
      this.loginError = '';

      try {
        const response = await fetch('http://localhost:3000/login', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            email: this.form.email,
            password: this.form.password,
          }),
        });

        const data = await response.json();

        if (!response.ok) {
          this.loginError = data.message || 'Invalid email or password';
          return;
        }

        localStorage.setItem('access_token', data.access_token);
        localStorage.setItem('user', JSON.stringify(data.user));

        alert(`Welcome back, ${data.user.name}!`);
      } catch (err) {
        this.loginError = 'Something went wrong. Please try again.';
      } finally {
        this.loading = false;
      }
    },
  },
};
</script>

<style scoped>
.form-container {
  width: 100%;
  max-width: 480px;
}

.welcome-title {
  font-family: 'Playfair Display', serif;
  font-size: 32px;
  font-weight: 700;
  color: #61227D;
  text-align: center;
  margin-bottom: 10px;
}

.welcome-subtitle {
  font-size: 14px;
  color: #666;
  text-align: center;
  line-height: 1.6;
  margin-bottom: 32px;
}

.login-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-options {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.remember-me {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}

.checkbox {
  width: 16px;
  height: 16px;
  accent-color: #61227D;
  cursor: pointer;
}

.checkbox-label {
  font-size: 14px;
  color: #444;
}

.forgot-password {
  font-size: 14px;
  font-weight: 600;
  color: #61227D;
  text-decoration: none;
  transition: opacity 0.2s;
}

.forgot-password:hover {
  opacity: 0.75;
}

.login-error {
  background: #fff5f5;
  border: 1px solid #fed7d7;
  color: #c53030;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 13px;
}

.sign-in-btn {
  width: 100%;
  padding: 14px;
  background: #61227D;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  font-family: 'DM Sans', sans-serif;
  cursor: pointer;
  transition: background 0.2s, transform 0.1s;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 50px;
}

.sign-in-btn:hover:not(:disabled) {
  background: #6a1faa;
}

.sign-in-btn:active:not(:disabled) {
  transform: scale(0.98);
}

.sign-in-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.loader {
  width: 20px;
  height: 20px;
  border: 2px solid rgba(255,255,255,0.4);
  border-top-color: #fff;
  border-radius: 50%;
  animation: spin 0.7s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

.signup-text {
  text-align: center;
  font-size: 14px;
  color: #666;
}

.signup-link {
  font-weight: 700;
  color: #61227D;
  text-decoration: none;
  transition: opacity 0.2s;
}

.signup-link:hover {
  opacity: 0.75;
}

.mobile-logo {
  display: none;
  flex-direction: column;
  align-items: center;
}

.mobile-logo-img {
  width: 200px;
  height: 150px;
}

@media (max-width: 768px) {
  .mobile-logo {
    display: flex;
  }
}
</style>