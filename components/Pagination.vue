<template>
  <div>
    <ul class="pagination">
      <li class="pagination-page">
        <button
          type="button"
          @click="onPreviousPageClicked" 
        >
          &laquo;
        </button>
      </li>
      <li class="pagination-page">
        <button
          type="button"
          @click="onNextPageClicked" 
        >
          &raquo;
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "pagination",
  props: [
    "limit",
    "offset",
  ],
  computed: {

  },
  methods: {
    onPreviousPageClicked() {
      this.$emit("updateOffset", this.offset - this.limit);
      
    },
    onNextPageClicked() {

      this.$emit("updateOffset", this.offset + this.limit)
      
    }
  },
};
</script>

