<template>
    <div class="container">
    <form action="">
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
        <textarea type="text" class="form-control" rows="5" v-model="content" :placeholder="contentPlaceholder"></textarea>
      </div>

      <div class="mb-3">
        <button class="btn btn-primary" @click.prevent="pageCreated({pageTitle, content})">Create Page</button>
      </div>
    </form>
  </div>
</template>

<script>

export default {
    props: {
        pageTitle: {
            type: String,
            default: ""
        },
        content: {
            type: String,
            default: ""
        },
        titlePlaceholder: {
            type: String,
            default: "Page Title"
        },
        contentPlaceholder: {
            type: String,
            default: "Page Content"
        },
        pageCreated:{
            type: Function,
            required: true
        }
    },
    data() {
        return{
            pageTitle: "",
            content: "",
            titlePlaceholder: "Page Title",
            contentPlaceholder: "Page Content"
        }
    },
    methods: {
        pageCreated(pageTitle, content) {
            console.log(pageTitle)
            console.log(content)
        }
    }
}
</script>