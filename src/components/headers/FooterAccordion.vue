<template>
  <div class="accordion-item">
    <button class="accordion-header" @click="isOpen = !isOpen">
      <span class="accordion-title">
        {{ title }}
      </span>

      <i
        class="fas fa-chevron-down accordion-icon"
        :class="{ open: isOpen }"
      ></i>
    </button>

    <transition
      name="accordion"
      @enter="enter"
      @after-enter="afterEnter"
      @leave="leave"
    >
      <div v-show="isOpen" class="accordion-content">
        <ul class="accordion-list">
          <li v-for="(item, index) in items" :key="index">
            <a :href="item.link">
              {{ item.label }}
            </a>
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },

    items: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      isOpen: false,
    };
  },

  methods: {
    enter(el) {
      el.style.height = "0";
      el.style.overflow = "hidden";
      el.style.transition = "height 0.35s ease";

      requestAnimationFrame(() => {
        el.style.height = el.scrollHeight + "px";
      });
    },

    afterEnter(el) {
      el.style.height = "auto";
      el.style.overflow = "visible";
    },

    leave(el) {
      el.style.height = el.scrollHeight + "px";
      el.style.overflow = "hidden";
      el.style.transition = "height 0.35s ease";

      requestAnimationFrame(() => {
        el.style.height = "0";
      });
    },
  },
};
</script>

<style scoped>
.accordion-item {
  border-bottom: 1px solid #d3d3d3;
}

.accordion-header {
  width: 100%;
  min-height: 65px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border: none;
  background: none;
  cursor: pointer;
  padding: 0;
}

.accordion-title {
  color: #fff;
  font-size: 15px;
  font-weight: 500;
}

.accordion-icon {
  color: #fff;
  font-size: 14px;
  transition: transform 0.3s ease;
}

.accordion-icon.open {
  transform: rotate(180deg);
}

.accordion-content {
  padding-bottom: 20px;
}

.accordion-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.accordion-list li {
  margin-bottom: 12px;
}

.accordion-list a {
  color: #fff;
  text-decoration: none;
  font-size: 13px;
  transition: opacity 0.2s;
}

.accordion-list a:hover {
  opacity: 0.8;
}
</style>
