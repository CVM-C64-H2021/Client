<template>
  <div>
    <ul class="pagination">
      <li class="pagination-page">
        <button
          type="button"
          @click="onFirstPageClicked"
          :disabled="isOnFirstPage"
          aria-label="Aller à la première page"
        >
          Première page
        </button>
      </li>
      <li class="pagination-page">
        <button
          type="button"
          @click="onPreviousPageClicked"
          :disabled="isOnFirstPage"
        >
          &laquo;
        </button>
      </li>
      <!-- <li v-for="page in pages" :key="page.name" class="pagination-page">
        <a
          href="#"
          @click="onPageClicked(page.name)"
          :disabled="page.isDisabled"
          class="{ active: isPageActive(page.name), last: (page.name == totalPages - 1 && Math.abs(page.name - currentPage) > 3), first:(page.name == 0 && Math.abs(page.name - currentPage) > 3) }"
        >
          {{ page.name }}
        </a>
      </li> -->
      <li class="pagination-page">
        <button
          type="button"
          @click="onNextPageClicked"
          :disabled="isOnLastPage"
        >
          &raquo;
        </button>
      </li>
      <li class="pagination-page">
        <button
          type="button"
          @click="onLastPageClicked"
          :disabled="isOnLastPage"
        >
          Dernière page
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "pagination",
  props: [
    "totalItems",
    "itemsPerPage",
    "currentPage",
    "totalPages",
  ],
  computed: {
    startVisiblePage() {
      if (this.currentPage === 1) {
        return 1;
      }

      if (this.currentPage === this.totalPages) {
       return this.totalPages + 1;
     }
       //if(this.currentPage != 0) {
           //return this.currentPage - 1;
       //}

       //return 0;
       
    },
    /*endVisiblePage() {
      return Math.min(this.startVisiblePage, this.totalPages);
    },
    maxVisiblePages() {

        if(this.totalPages > 3) {

            return 3;
        }
        else {

            return this.totalPages;
        }
    },
    pages() {
      const pageRange = [];

      for (let i = 1; i <= this.totalPages; i++) {
        pageRange.push({
          name: i,
          isDisabled: i === this.currentPage,
        });
      }

      return pageRange;
    },*/
    isOnFirstPage() {
      return this.currentPage === 1 || this.totalPages === 1;
    },
    isOnLastPage() {
      return this.currentPage === this.totalPages;
    },
  },
  methods: {
    onPageChanged(page) {
      this.$emit("onPageChanged", page);
    },
    onFirstPageClicked() {
      this.$emit("onPageChanged", 1);
    },
    onPreviousPageClicked() {
      this.$emit("onPageChanged", this.currentPage - 1);
    },
    onPageClicked(pageNumber) {
      this.$emit("onPageChanged", pageNumber);
    },
    onNextPageClicked() {
      this.$emit("onPageChanged", this.currentPage + 1);
    },
    onLastPageClicked() {
      this.$emit("onPageChanged", this.totalPages);
    },
    isPageActive(pageNumber) {
      return this.currentPage == pageNumber;
    },
  },
  filters: {
    paginate(resultItems) {
        this.resultCount = resultItems.length;

        if (this.currentPage >= this.totalPages) {
          this.currentPage = this.totalPages - 1;
        }
        var index = this.currentPage * this.itemsPerPage;
        return list.slice(index, index + this.itemsPerPage)
    },
  }
};
</script>

