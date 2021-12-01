<template>
  <div class="home-container">
    <HomeIntro />
    <BrandList />
    <BaseSectionHeader>
      <template #sub-title> What I do best </template>
      <template #main-title> Specialisation </template>
    </BaseSectionHeader>
    <SpecialisationList />
    <BaseSectionHeader>
      <template #sub-title> Projects that are clients love </template>
      <template #main-title> Works </template>
      <template #button>
        <BaseButton>Explore all projects</BaseButton>
      </template>
    </BaseSectionHeader>
    <WorksList />
    <BaseSectionHeader>
      <template #sub-title> My weekly newsletter and blogs </template>
      <template #main-title> Design newsletter </template>
      <template #button>
        <BaseButton>Explore all blogs</BaseButton>
      </template>
    </BaseSectionHeader>
    <SwiperComp />
    <BaseSectionHeader :noSubTitle="true" :isCentered="true">
      <template #main-title> Let's connect </template>
      <template #content>
        <p class="content">Got a project feel free to get in touch</p>
      </template>
      <template #link
        ><button class="link-button">
          Sukura@haruno.com&nbsp;&nbsp;&nbsp;<i
            class="fas fa-arrow-right"
          ></i></button
      ></template>
    </BaseSectionHeader>
    <ContactForm />
    <FooterNav />
  </div>
</template>

<script>
import HomeIntro from "../components/home/HomeIntro.vue";
import BrandList from "../components/home/BrandList.vue";
import BaseSectionHeader from "../components/home/BaseSectionHeader.vue";
import SpecialisationList from "../components/home/SpecialisationList.vue";
import WorksList from "../components/home/WorksList.vue";
import BaseButton from "../components/home/BaseButton.vue";
import SwiperComp from "../components/home/SwiperComp.vue";
import ContactForm from "../components/home/ContactForm.vue";
import FooterNav from "../components/footer/FooterNav.vue";
export default {
  name: "Home-comp",
  components: {
    HomeIntro,
    BrandList,
    BaseSectionHeader,
    SpecialisationList,
    WorksList,
    BaseButton,
    SwiperComp,
    ContactForm,
    FooterNav,
  },
};
</script>

<style lang="scss">
.home-container {
  width: 90%;
  max-width: 1140px;
  margin: 0 auto;
}
</style>
