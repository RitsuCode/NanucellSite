<template>
  <div>
    <Navbar />
    <Hero />
    <Benefits />
    <DoctorsSection />
    <ProductsGrid />
    <BestSeller />
    <Packages />
    <CustomerReviews />
    <VideoTestimonials />
    <Contacts />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import Benefits from './components/Benefits.vue'
import DoctorsSection from './components/DoctorsSection.vue';
import ProductsGrid from './components/ProductsGrid.vue';
import BestSeller from './components/BestSeller.vue';
import Packages from './components/Packages.vue';
import CustomerReviews from './components/CustomerReviews.vue';
import VideoTestimonials from './components/VideoTestimonials.vue';
import Contacts from './components/Contacts.vue';



export default {
  name: 'App',
  components: {
    Navbar,
    Hero,
    Benefits,
    DoctorsSection,
    ProductsGrid,
    BestSeller,
    Packages,
    CustomerReviews,
    VideoTestimonials,
    Contacts
  }
}
</script>