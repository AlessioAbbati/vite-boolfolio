<script>
export default {

}
</script>

<template>
  <h1>contact us</h1>

  <form>
      <div class="mb-3">
        <label for="name" class="form-label">Name</label>
        <input type="name" class="form-control" id="name" aria-describedby="emailHelp">
      </div>

      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Email address</label>
        <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
      </div>

      <!-- TODO: aggiungi textarea -->

      <div class="mb-3 form-check">
        <input type="checkbox" class="form-check-input" id="exampleCheck1">
        <label class="form-check-label" for="exampleCheck1">subscribe to newsletter</label>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</template>

<style lang="scss" scoped>

</style>



