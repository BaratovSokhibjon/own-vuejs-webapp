<template>
  <navbar :pages="pages" :active-page="activePage" :nav-link-click="(index) => activePage = index" />
  <page-viewer :page="pages[activePage]" />
</template>

<script>
import Navbar from './components/Navbar.vue';
import PageViewer from './components/PageViewer.vue';

export default {
  components: {
    Navbar,
    PageViewer
  },
  data() {
    return {
      activePage: 0,
      pages: [
        {
          title: 'Home Title',
          content: 'Home Content',
          link: { name: 'Home', url: 'index.html' }
        },
        {
          title: 'About Title',
          content: 'About Content',
          link: { name: 'About', url: 'about.html' }
        },
        {
          title: 'Contact Title',
          content: 'Contact Content',
          link: { name: 'Contact us', url: 'contacts.html' }
        }
      ]
    }
  }
}
</script>