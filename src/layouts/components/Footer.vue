<template>
  <div class="h-100 d-flex align-center justify-space-between text-medium-emphasis">
    <!-- 👉 Footer: left content -->
    <div class="d-flex align-center text-base">
      &copy;
      {{ new Date().getFullYear() }},
      Made With
      <VIcon
        icon="ri-heart-fill"
        color="error"
        size="1.25rem"
        class="mx-1"
      />
      By <a
        href="https://www.gxuwz.edu.cn/"
        target="_blank"
        rel="noopener noreferrer"
        class="text-primary ms-1"
      >梧州学院&香港教育大学</a>
    </div>
  </div>
</template>
