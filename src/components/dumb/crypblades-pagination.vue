<template>
		<b-pagination
			v-model="page"
			:total-rows="totalRows"
			:per-page="perPage"
			v-on:change="onChangePage($event)"
		>
		</b-pagination>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
	props: [
		'totalRows', 
		'perPage',
		'page'
	],
	name: 'CryptobladesPagination',
	components: {},
	data() {
      return { 
          itemsPerPage : this.perPage,
		  totalItems: this.totalRows,
		  curPage: this.page
	  }
    },
	watch: {
		// totalRows: function(val) {
		// 	this.totalItems = val;
		// },
		// perPage: function(val) {
		// 	this.itemsPerPage = val;
		// }
	},
	methods: {
		onChangePage(page: number) {
			this.$emit('changes', page)
		}
	}
})
</script>

<style scoped>

	::v-deep .page-item {
		margin-right: 0.5rem;
		font-size: 0.75rem;
	}

	::v-deep .page-item.active .page-link {
		background: #43506A !important;
		border: 1px solid #43506A !important;
		color: #FFFFFF;
	}
	
	::v-deep .page-item .page-link {
		color: #FFFFFF !important;
		background: #FFFFFF00 !important;
		border: 1px solid #43506A !important;
	}

	::v-deep .page-link {
		border-radius: 5px !important;
	}

</style>
