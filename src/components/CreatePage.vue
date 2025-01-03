<template>
    <div class="container">
        <form action="">
            <div class="row">
                <div class="container col-md-8">
                    <div class="my-3">
                        <label for="" class="form-label">
                            Page Title
                        </label>
                        <input type="text" class="form-control" v-model="title" :placeholder="titlePlaceholder" />
                    </div>

                    <div class="mb-3">
                        <label for="" class="form-label">
                            Page content
                        </label>
                        <textarea type="text" class="form-control" rows="5" v-model="content"
                            :placeholder="contentPlaceholder"></textarea>
                    </div>
                </div>

                <div class="col">
                    <div class="my-3">
                        <label for="" class="form-label">Link Text</label>
                        <input type="text" class="form-control" v-model="name">
                    </div>

                    <div class="mb-3">
                        <label for="" class="form-label">Link URL</label>
                        <input type="text" class="form-control" v-model="url">
                    </div>

                    <div class="row mb-3">
                        <div class="form-check">
                            <input type="checkbox" class="form-check-input" v-model="published">
                            <label class="form-check-label" for="">Published</label>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="mb-3">
                <button class="btn btn-primary" @click.prevent="submitForm()" :disabled="isFormInvalid()">Create Page</button>
            </div>

        </form>
    </div>
</template>

<script>

export default {
    props: {
        pageCreated: {
            type: Function,
            required: true
        },
        isFormInvalid: {
            type: Function,
            required: true
        }
    },
    data() {
        return {
            title: "",
            content: "",
            name: "",
            url: "",
            titlePlaceholder: "Page Title",
            contentPlaceholder: "Page Content",
            published: true
        }
    },
    methods: {
        submitForm() {
            if (!this.title || !this.content || !this.name || !this.url) {
                alert("Please fill in the form");
                return;
            }

            this.pageCreated({
                title: this.title,
                content: this.content,
                link: {
                    name: this.name,
                    url: this.url
                },
                published: this.published
            });

            this.title =  "",
            this.content =  "",
            this.name =  "",
            this.url =  "",
            this.titlePlaceholder =  "Page Title",
            this.contentPlaceholder =  "Page Content",
            this.published =  true
        },

        isFormInvalid() {
            return !this.title || !this.content || !this.name || !this.url;
        }
    },

    watch: {
        title(newTitle, oldTitle){
            if (this.name === oldTitle ){
                this.name = newTitle
            }
        }
    }
}
</script>