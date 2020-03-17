<template>

    <component :is="getLayout" :allitems="allBlogPosts"></component>
</template>

<script>
import BaelGrid from "~/components/BaelGrid";
import FullGrid from "~/components/FullGrid";
export default {
    watchQuery: ['page'],

   transition (to, from) {
     
    if (!from) return 'fade'
    return +to.query.page > +from.query.page ? 'slide-right' : 'slide-left'
  },
  name: "Index",
  components: { BaelGrid,FullGrid },
  data() {
    return {};
  },
  methods: {},

  computed: {
    allBlogPosts() {
      return this.$store.state.blogPosts;
    },
    getLayout() {
if (this.$store.state.siteInfo.altlayout == false ) {
  return 'BaelGrid'
} else if (this.$store.state.siteInfo.altlayout == true ) {
  return 'FullGrid'
}

    }
  }
};
</script>

<style>

.item .full-bg-link{
  background-color: #c40093;
  color: #ffffff;
}

a {
  color: #c40093;
}

.item:hover .full-bg-image{
  opacity: 1;
  transition: .2s all;
}

.item .full-bg-image{
  opacity: .8;
  transition: .2s all;
  width: 100%;
}

.browse a {
  width: 100%;
}
.search:focus {
  outline: none;
}
.footer__heading {
  text-transform: uppercase;
}
nav .r {
  grid-gap: 0;
}
.r.full-height {
  grid-gap: 0;
}
@media only screen and (max-width: 40rem) {
  .xs-collapse {
    visibility: hidden;
    visibility: collapse;
    border: 0 !important;
    border-color: none !important;
    padding: 0 !important;
  }
  .xs-visible {
    visibility: visible;
  }
  
}
</style>
