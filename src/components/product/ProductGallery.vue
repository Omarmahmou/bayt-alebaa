<template>
  <div class="gallery">
    <div class="gallery-thumbs">
      <div
        v-for="(image, index) in images"
        :key="index"
        class="thumb"
        @click="selectImage(index)"
      >
        <img :src="image" alt="" />
      </div>
    </div>

    <div class="gallery-main">
      <transition name="slide" mode="out-in">
        <img :key="currentImage" :src="currentImage" alt="product" />
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductGallery",

  props: {
    images: { type: Array, default: () => [] },
  },

  data() {
    return {
      selectedIndex: 0,
    };
  },

  computed: {
    currentImage() {
      return this.images[this.selectedIndex] || "";
    },
  },

  methods: {
    selectImage(index) {
      this.selectedIndex = index;
    },
  },
};
</script>

<style scoped>
.gallery {
  display: grid;
  grid-template-columns: 80px 1fr;
  gap: 10px;
}

.gallery-thumbs {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-top: 20px;
}

.thumb {
  overflow: hidden;
  cursor: pointer;
}

.thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.gallery-main {
  overflow: hidden;
}

.gallery-main img {
  width: 100%;
  display: block;
  aspect-ratio: 4 / 3;
  object-fit: cover;
}

/* transition */
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.4s ease;
}

.slide-enter {
  transform: translateX(100%);
}

.slide-leave-to {
  transform: translateX(-100%);
}

@media (max-width: 1000px) {
  .gallery {
    display: flex;
    flex-direction: column;
    max-width: 750px;
    margin: 0 auto;
  }

  .gallery-main {
    order: 1;
    width: 100%;
  }

  .gallery-main img {
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
  }

  .gallery-thumbs {
    order: 2;
    flex-direction: row;
    justify-content: center;
    gap: 10px;
    margin-top: 15px;
  }

  .thumb {
    width: 70px;
    height: 70px;
    flex-shrink: 0;
  }
}
</style>
