<template>
    <nav id="navbar"
        :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup"
                aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
                <div class="navbar-nav">
                    <li v-for="(page, index) in publishedPages" :key="index" class="nav-link">
                        <navbar-link :page="page" :is-active="activePage === index" @click.prevent="navLinkClick(index)" />
                    </li>
                </div>
            </div>
            <form>
                <button class="btn btn-primary" @click.prevent="changeTheme()">
                    Toggle Navbar
                </button>
            </form>
        </div>
    </nav>
</template>

<script>
import NavbarLink from "./NavbarLink.vue"

export default {
    components: {
        NavbarLink
    },
    
    name: 'navbar',
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
        this.getThemeSetting();
    },
    
    data() {
        return {
            theme: 'light'
        }
    },

    computed: {
        publishedPages() {
            return this.pages.filter(page => page.published);
        }
    },

    methods: {
        changeTheme() {
            this.theme = this.theme === 'light' ? 'dark' : 'light';
            this.setThemeSetting();
        },

        setThemeSetting() {
            localStorage.setItem('theme', this.theme)
        },

        getThemeSetting() {
            let theme = localStorage.getItem('theme')

            if (theme) {
                this.theme = theme
            }
        }

    }
}

</script>