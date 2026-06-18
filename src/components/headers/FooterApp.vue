<template>
  <footer>
    <div class="container">
      <div class="footer-top">
        <FooterContact />

        <div class="footer-sections desktop-sections">
          <FooterSection title="عن بيت الإباء" :items="aboutItems" />
          <FooterSection title="الدعم" :items="supportItems" />
          <FooterSection title="روابط سريعة" :items="linksItems" />
        </div>

        <div class="mobile-sections">
          <FooterAccordion title="عن بيت الإباء" :items="aboutItems" />
          <FooterAccordion title="الدعم" :items="supportItems" />
          <FooterAccordion title="روابط سريعة" :items="linksItems" />
        </div>
      </div>
      <FooterBottom />
    </div>
  </footer>
</template>

<script>
import FooterAccordion from "./FooterAccordion.vue";
import FooterBottom from "./FooterBottom.vue";
import FooterContact from "./FooterContact.vue";
import FooterSection from "./FooterSection.vue";

export default {
  data() {
    return {
      aboutItems: [
        { label: "من نحن", link: "#" },
        { label: "المعارض", link: "#" },
        { label: "المشاريع", link: "#" },
        { label: "سياسة الخصوصية", link: "#" },
      ],

      supportItems: [{ label: "اتصل بنا", link: "#" }],

      linksItems: [
        { label: "أسئلة متكررة", link: "#" },
        { label: "سياسة الضمان", link: "#" },
        { label: "الإستبدال والإسترجاع", link: "#" },
        { label: "الوظائف", link: "#" },
      ],
    };
  },
  components: {
    FooterContact,
    FooterSection,
    FooterBottom,
    FooterAccordion,
  },
};
</script>

<style scoped>
footer {
  background-color: #02426a;
  font-family: "Cairo", sans-serif;
  font-weight: 500;
}

.container {
  max-width: 1300px;
  /* margin: auto; */
  padding: 18px 20px 0;
}

.footer-top {
  display: flex;
  justify-content: space-between;
  gap: 60px;
  flex-wrap: wrap;
}

.footer-sections {
  flex: 1;
  display: flex;
  justify-content: space-between;
}

.mobile-sections {
  display: none;
}
@media (max-width: 1000px) {
  .footer-top {
    flex-direction: column;
    gap: 25px;
  }

  .desktop-sections {
    display: none;
  }

  .mobile-sections {
    display: block;
  }
  .container {
    max-width: 750px;
    /* margin: auto; */
    padding: 18px 20px 0;
  }
}
</style>
