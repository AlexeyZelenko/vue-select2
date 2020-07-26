<template>
	<div class="v-table-row">
		<div class="row row__name">{{row_data.name}}</div>
		<div class="row row__earned">{{row_data.phone}}</div>
		<div class="row row__spend">{{row_data.username}}</div>
		<div class="row row__dte">{{row_data.website}}</div>
	</div>
</template>

<script>
  export default {
    name: "",
    data: () => ({

    }),
    // components: {},
    methods: {},
    computed: {},
    watch: {},
    props: {
      row_data: {
        type: Object,
        default: () => {
            return {}
        }
      }
    },
  }
</script>

<style>
	.v-table-row {
		display: flex;
		justify-content: space-around;
	}
	.row {
		flex-basis: 25%;
		padding: 8px 16px;
		text-align: left;
		}

</style>