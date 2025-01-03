<template>
    <div class="container">
    <form action="">
      <div class="my-3">
        <label for="" class="form-label">
          Page Title
        </label>
        <input type="text" class="form-control" :value="pageTitle" @input="(event) => pageTitle = event.target.value" />
      </div>

      <div class="mb-3">
        <label for="" class="form-label">
          Page content
        </label>
        <textarea type="text" class="form-control" rows="5"></textarea>
      </div>

      <div class="mb-3">
        <button class="btn btn-primary" @click.prevent="pageCreated({pageTitle})">Create Page</button>
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
        pageCreated:{
            type: Function,
            required: true
        }
    },
    data() {
        return{
            pageTitle: ''
        }
    },
    methods: {
        pageCreated(pageTitle) {
            console.log(pageTitle)
        }
    }
}
</script>