<template>
	<div class="v-table">
		<div class="v-table__header">
			<p>
				Name
				<i class="material-icons">
					unfold_more
				</i>
			</p>
			<p>Phone
				<i class="material-icons">
					unfold_more
				</i>
			</p>
			<p>Username
				<i class="material-icons">
					unfold_more
				</i>
			</p>
			<p>Website
				<i class="material-icons">
					unfold_more
				</i>
			</p>
		</div>
		<div class="v-table__body">
			<v-table-row
					:key="row.id"
					:row_data="row"
					v-for="row in paginatedUsers"
			/>
		</div>
		<div class="v-table__pagination">
			<div
					class="page"
					v-for="page in pages"
					:key="page"
					:class="{'page_selected': page === pagesNumber}"
					@click="pageClick(page)"
			>
				{{page}}
			</div>
		</div>
	</div>
</template>


<script>
    import vTableRow from './v-table-row'

    export default {
        name: "",
        data: () => ({
            usersPerPage: 5,
            pagesNumber: 1
        }),
        components: {
            vTableRow
        },
        methods: {
            pageClick(page) {
						this.pagesNumber = page;
            }
        },
        computed: {
            pages() {
                return Math.ceil(this.users_data.length / 5)
            },
            paginatedUsers() {
                let from = (this.pagesNumber - 1) * this.usersPerPage;
                let to = from + this.usersPerPage;
                return this.users_data.slice(from, to);
            }
        },
        watch: {},
        props: {
            users_data: {
                type: Array,
                default: () => {
                    return []
                },
            }
        }
    }
</script>

<style>
	.v-table {
		max-width: 900px;
		margin: 0 auto;
	}

	.v-table__header {
		display: flex;
		justify-content: space-around;
		border-bottom: solid 1px #2c3e50;
	}

	.v-table__header p {
		/*flex-basis: 25%;*/
		/*text-align: center;*/
	}

	.v-table__pagination {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
	}

	.page {
		padding: 8px;
		border: solid 1px #e7e7
	}
	.page:hover {
		background: #b6c9b6;
		cursor: pointer;
		color: whitesmoke;
	}
	.page_selected {
		background: #b6c9b6;
		cursor: pointer;
		color: whitesmoke;
	}
</style>