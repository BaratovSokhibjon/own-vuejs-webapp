<template>
    <a  
        class="nav-link"
        aria-current="page" 
        :class="activeClasses"
        :href="page.link.url"
    >{{page.link.name}}</a>
</template>

<script>

export default {
    props: {
        page: {
            type: Object,
            default() {
                return {
                    pageTitle: '',
                    content: ''
                }
            }
        },
        isActive: {
            type: Boolean,
            default: false
        }
    },
    
    computed: {
        activeClasses() {
            return {
                active: this.isActive,
                emphasize: this.isActive
            };
        }
    }
}

</script>

<style scoped>
.emphasize {
    text-decoration: underline !important;
}
</style>