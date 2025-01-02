<template>
  <navbar :pages="pages" :active-page="activePage" :nav-link-click="navLinkClick" />
  <page-viewer v-if="pages.length > 0" :page="pages[activePage]" />
</template>

<script>
import Navbar from './components/Navbar.vue';
import PageViewer from './components/PageViewer.vue';

export default {
  components: {
    Navbar,
    PageViewer
  },
  props: {
    pages: {
        type: Array,
        default() {
            return [];
        }
    },
    activePage: {
        type: Number,
        default: 0
    },
    navLinkClick: {
        type: Function,
        required: true
    }
  },
  created() {
    this.fetchData()
  },
  data() {
    return {
      activePage: 0,
      pages: []
    }
  },
  methods: {
    async fetchData() {
      let res = await fetch('data.json');
      let data = await res.json();
      console.log(data)
      this.pages = data;
    },
    navLinkClick(index) {
      this.activePage = index;
    }
  }
}
</script>