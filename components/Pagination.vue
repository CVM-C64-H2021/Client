<template>
  <div>
    <ul class="pagination">
      <li class="pagination-page">
        <button
          type="button"
          @click="onPreviousPageClicked" 
          :disabled="isOnFirstPage"
        >
          &laquo;
        </button>
      </li>
      <li class="pagination-page">
        <button
          type="button"
          @click="onNextPageClicked" 
          :disabled="isOnLastPage"
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
    "itemCount",
    "limit",
    "offset",
  ],
  computed: {
    isOnFirstPage() {
      return this.offset -= this.limit > 0;
    },
    hasPreviousPage() {
      return this.offset -= this.limit > 0;
    },
    isOnLastPage() {
      return this.itemsCount < this.limit;
    },
  },
  methods: {
    onPreviousPageClicked() {

      if(!isOnFirstPage) {
        this.$emit("updateOffset", this.offset -= this.limit);
      }
    },
    onNextPageClicked() {
      if(!isOnLastPage) {
        this.$emit("updateOffset", this.offset += this.limit)
      }
    }
  },
};
</script>

