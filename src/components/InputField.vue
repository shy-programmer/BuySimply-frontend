<template>
  <div class="field-group">
    <label class="field-label">
      {{ label }} <span class="required">*</span>
    </label>
    <div class="input-wrapper">
      <input
        :type="inputType"
        :value="modelValue"
        :placeholder="placeholder"
        class="field-input"
        :class="{ 'input-error': error }"
        @input="$emit('update:modelValue', $event.target.value)"
      />
      <button
        v-if="isPassword"
        type="button"
        class="toggle-password"
        @click="$emit('toggle')"
      >
        <svg v-if="!showPassword" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/>
          <circle cx="12" cy="12" r="3"/>
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94"/>
          <path d="M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19"/>
          <line x1="1" y1="1" x2="23" y2="23"/>
        </svg>
      </button>
    </div>
    <span v-if="error" class="error-text">{{ error }}</span>
  </div>
</template>

<script>
export default {
  name: 'InputField',
  props: {
    label: { type: String, required: true },
    modelValue: { type: String, default: '' },
    placeholder: { type: String, default: '' },
    isPassword: { type: Boolean, default: false },
    showPassword: { type: Boolean, default: false },
    error: { type: String, default: '' },
  },
  emits: ['update:modelValue', 'toggle'],
  computed: {
    inputType() {
      if (!this.isPassword) return 'text';
      return this.showPassword ? 'text' : 'password';
    },
  },
};
</script>

<style scoped>
.field-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.field-label {
  font-size: 14px;
  font-weight: 500;
  color: #1a1a2e;
}

.required {
  color: #e53e3e;
  margin-left: 2px;
}

.input-wrapper {
  position: relative;
}

.field-input {
  width: 100%;
  padding: 12px 16px;
  border: 1.5px solid #e0e0e0;
  border-radius: 8px;
  font-size: 14px;
  font-family: 'DM Sans', sans-serif;
  color: #1a1a2e;
  background: #fff;
  transition: border-color 0.2s;
  outline: none;
}

.field-input::placeholder {
  color: #aaa;
}

.field-input:focus {
  border-color: #7B2FBE;
}

.field-input.input-error {
  border-color: #e53e3e;
}

.toggle-password {
  position: absolute;
  right: 14px;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  color: #999;
  display: flex;
  align-items: center;
  padding: 0;
  transition: color 0.2s;
}

.toggle-password:hover {
  color: #7B2FBE;
}

.error-text {
  font-size: 12px;
  color: #e53e3e;
}
</style>