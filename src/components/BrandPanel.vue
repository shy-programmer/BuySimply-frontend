<template>
  <div class="left-panel">
    <div class="brand">
      <div class="logo">
        <svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="24" cy="12" r="8" fill="#7B2FBE" opacity="0.85"/>
          <circle cx="14" cy="28" r="7" fill="#F5A623" opacity="0.9"/>
          <circle cx="34" cy="28" r="7" fill="#7B2FBE" opacity="0.6"/>
          <path d="M24 20 L14 28 L24 36 L34 28 Z" fill="white" opacity="0.3"/>
        </svg>
      </div>
      <span class="brand-name">Team Achieve</span>
    </div>

    <div class="image-container">
      <div class="image-placeholder">
        <img
          src="https://images.unsplash.com/photo-1529156069898-49953e39b3ac?w=600&q=80"
          alt="Team celebrating"
          class="hero-image"
        />
      </div>
    </div>

    <div class="left-footer">
      <p class="company-title">Team Achieve</p>
      <p class="company-tagline">Your perfect solution for funding your desires</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BrandPanel',
};
</script>

<style scoped>
.left-panel {
  width: 42%;
  background: #f3eeff;
  display: flex;
  flex-direction: column;
  padding: 32px;
}

.brand {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 32px;
}

.brand-name {
  font-weight: 600;
  font-size: 16px;
  color: #1a1a2e;
}

.image-container {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-placeholder {
  width: 100%;
  max-width: 420px;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 8px 32px rgba(123, 47, 190, 0.15);
}

.hero-image {
  width: 100%;
  height: 320px;
  object-fit: cover;
  display: block;
}

.left-footer {
  text-align: center;
  padding-top: 24px;
}

.company-title {
  font-weight: 700;
  font-size: 20px;
  color: #7B2FBE;
  margin-bottom: 6px;
}

.company-tagline {
  font-size: 14px;
  color: #555;
  line-height: 1.5;
}

@media (max-width: 768px) {
  .left-panel {
    width: 100%;
    padding: 24px;
  }

  .hero-image {
    height: 220px;
  }
}
</style>