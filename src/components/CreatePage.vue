<template>
    <div class="container">
        <form action="">
            <div class="row">
                <div class="container col-md-8">
                    <div class="my-3">
                        <label for="" class="form-label">
                            Page Title
                        </label>
                        <input type="text" class="form-control" v-model="pageTitle" :placeholder="titlePlaceholder" />
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
                        <input type="text" class="form-control" v-model="linkText">
                    </div>

                    <div class="mb-3">
                        <label for="" class="form-label">Link URL</label>
                        <input type="text" class="form-control" v-model="linkURL">
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
            pageTitle: "",
            content: "",
            linkText: "",
            linkURL: "",
            titlePlaceholder: "Page Title",
            contentPlaceholder: "Page Content"
        }
    },
    methods: {
        submitForm() {
            if (!this.pageTitle || !this.content || !this.linkText || !this.linkURL) {
                alert("Please fill in the form");
                return;
            }

            this.pageCreated({
                title: this.pageTitle,
                content: this.content,
                link: {
                    text: this.linkText,
                    url: this.linkURL
                }
            });

        },

        isFormInvalid() {
            return !this.pageTitle || !this.content || !this.linkText || !this.linkURL;
        }
    }
}
</script>