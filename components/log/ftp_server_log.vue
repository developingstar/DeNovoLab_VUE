<template>
	<div class="container-fluid">
		<div class="row">
			<div class="wrapper single">
				<time-display></time-display>
				<ol class="breadcrumb">
					<li class="breadcrumb-item">
						<a>Log</a>
					</li>
					<li class="breadcrumb-item active">FTP Server Log</li>
				</ol>
				<h1 class="page-header">FTP Server Log</h1>
				<div class="timeline">
					<div class="chart_select_header grided">
						<div class="col-md-3 col-sm-4">
							<label>Period:</label>
							<select2 :options="options" v-model="period">
								<option disabled value="0">Select one</option>
							</select2>
						</div>
						<div class="col-md-6 col-sm-6">
							<div class="inlined">
								<label for="submitted_time1" class="m-top-15"></label>
								<!-- <input type="text" name="submitted_time1" v-model="submitted_time1" class="form-control" placeholder="Enter Date/Time"> -->
								<el-date-picker style="width: 100%;" type="datetime" v-model="submitted_time1" :picker-options="{}" placeholder="Enter Date and TIme"></el-date-picker>
							</div>
							<div class="inlined">
								<label for="submitted_time2" class="m-top-15"></label>
								<!-- <input type="text" name="submitted_time2" v-model="submitted_time2" class="form-control" placeholder="Enter Date/Time"> -->
								<el-date-picker style="width: 100%;" type="datetime" v-model="submitted_time2" :picker-options="{}" placeholder="Enter Date and TIme"></el-date-picker>
							</div>
						</div>
						<div class="col-md-3 col-sm-2">
							<label>GMT:</label>
							<select2 :options="options" v-model="gmt">
								<option disabled value="0">Select one</option>
							</select2>
						</div>
						<div class="clearfix little-space"></div>
						<div class="col-md-3 col-sm-4">
							<a class="btn btn-primary m-top-10">
								Query
							</a>
						</div>
						<div class="clearfix"></div>
					</div>
					<div class="chart_content">
						<div class="table_filters marged-40">
							<div class="inline-block select_min_wrapper">
								<span class="inline-block">Page row:</span>
								<select2 :options="options" v-model="selected1" class="inline-block">
								</select2>
							</div>
							<div class="inline-block">
								<select2 :options="options" v-model="selected2">
									<option disabled value="0">Show/Hide Columns</option>
								</select2>
							</div>
						</div>
						<div class="col-md-12">
							<div class="table-responsive marged-30">
								<table class="table table-striped table-hover carrier_groups originators">
									<thead>
										<tr>
											<th></th>
											<th></th>
											<th></th>
											<th></th>
											<th></th>
										</tr>
									</thead>
									<tbody>
										<tr>
											<td></td>
											<td></td>
											<td></td>
											<td></td>
											<td></td>
										</tr>
									</tbody>
								</table>
							</div>
							<div class="pull-right pagination m-r-30">
								<pagination :current-page="pageOne.currentPage" :total-pages="pageOne.totalPages" @page-changed="pageOneChanged">
								</pagination>
							</div>
						</div>
					</div>
					<div class="clearfix"></div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>   
const vSelect = require('vue!../main_components/select.vue'),
	Pagination = require('vue!../main_components/pagination.vue');
module.exports = {
	components: {
		'select2': vSelect,
		'pagination': Pagination
	},
	data: function () {
		return {
			pageOne: {
				currentPage: 1,
				totalPages: 10
			},
			period: '',
			submitted_time1: '',
			submitted_time2: '',
			options: [
				{ id: 1, value: 'carrier1', text: 'Carrier 1' },
				{ id: 2, value: 'carrier2', text: 'Carrier 2' },
				{ id: 3, value: 'carrier3', text: 'Carrier 3' },
				{ id: 4, value: 'carrier4', text: 'Carrier 4' },
				{ id: 5, value: 'carrier5', text: 'Carrier 5' }
			],
			selected1: 1,
			selected2: 1
		}
	},
	methods: {
		pageOneChanged(pageNum) {
			this.pageOne.currentPage = pageNum
		}
	},
	mounted: function () {

	}
}
</script>

<style>

</style>
