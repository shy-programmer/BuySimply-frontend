<template>
  <div class="left-panel">
    <div class="brand">
      <div class="logo">
        <img src="../assets/brand_logo.png" alt="Logo" class="logo-img" />
      </div>
    </div>

    <div class="image-container">
      <div class="image-placeholder">
        <img
          src="../assets/brand_image.png"
          alt="Brand image"
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
  background: #F8EAFF;
  display: flex;
  flex-direction: column;
  padding: 32px;
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
  height: 300px;
  display: block;
}

.left-footer {
  text-align: center;
  padding-top: 20px;
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

.logo-img {
  width: 170px;
  height: 80px;
}

@media (max-width: 768px) {
  .left-panel {
    display: none
  }

  .image-container {
    display: none;
  }

  .left-footer {
    display: none;
  }
  
}
</style>