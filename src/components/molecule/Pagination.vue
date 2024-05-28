<template>
<div>
    <div>      
        Showing {{ startEntry }} to {{ endEntry }} of {{ totalEntries }} entries
    </div>
    <div class="page-input">
      <label>Enter wanted page number</label>
      <input
        type="number"
        v-model="inputPage"
        @input="validatePageNumber"
        @keyup="goToInputPage"
        :min="1"
        :max="totalPages"
        placeholder="Your page"
      />
    </div> 
    <div class="pagination">
    <button @click="prevPage" :disabled="currentPage === 1">Previous</button>
     <span v-for="page in pagesToShow" :key="page" :class="{ 'active-page': currentPage === page }" @click="goToPage(page)">
      {{ page }}
    </span>
     <button @click="nextPage" :disabled="currentPage === totalPages">Next</button>
  </div>
</div>
</template>

<script>
export default {
   props: ["currentPage", "totalPages", "totalEntries", "entriesPerPage"],
   data() {
    return {
      inputPage: this.currentPage,
    };
  },
  watch: {
    currentPage(newVal) {
      this.inputPage = newVal;
    },
  },
   computed: {
     startEntry() {
      return (this.currentPage - 1) * this.entriesPerPage + 1;
    },
    endEntry() {
      const end = this.currentPage * this.entriesPerPage;
      return end > this.totalEntries ? this.totalEntries : end;
    },
    pagesToShow() {
      if (this.totalPages <= 5) {
        return Array.from({ length: this.totalPages }, (_, i) => i + 1);
      }
      if (this.currentPage <= 3) {
        return [1, 2, 3, '...', this.totalPages];
      }
      if (this.currentPage >= this.totalPages - 2) {
        return [1, '...', this.totalPages - 2, this.totalPages - 1, this.totalPages];
      }
      return [1, '...', this.currentPage - 1, this.currentPage, this.currentPage + 1, '...', this.totalPages];
    },
  },
  methods: {
    prevPage() {
      if (this.currentPage > 1) {
        this.$emit('update:currentPage', this.currentPage - 1);
      }
    },
    nextPage() {
        console.log("asdnasdj")
      if (this.currentPage < this.totalPages) {
        this.$emit('update:currentPage', this.currentPage + 1);
      }
    },
    goToPage(page) {
      if (page !== '...') {
        this.$emit('update:currentPage', page);
      }
    },
     goToInputPage() {
      if (this.inputPage >= 1 && this.inputPage <= this.totalPages) {
        this.$emit('update:currentPage', this.inputPage);
      }
    },
    validatePageNumber() {
        console.log(this.inputPage, this.totalPages)
        if(this.inputPage > this.totalPages) {
            this.inputPage = 1
        }
    },
  },
};
</script>

<style scoped>
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
.active-page {
    border: 1px solid;
}
</style>
