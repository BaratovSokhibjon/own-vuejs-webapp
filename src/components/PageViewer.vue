<template>
    <div class="container">
        <h1>{{page.title}}</h1>
        <p>{{page.content}}</p>
    </div>
</template>

<script>

export default{
    name: "page-viewer",
    props: {
        page: {
            type: Object,
            default() {
                return {
                    pageTitle: '',
                    content: ''
                }
            }
        }
    }
}

</script>