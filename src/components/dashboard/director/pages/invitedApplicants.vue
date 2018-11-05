<template>
	<div>
		<loader v-if="loading" />
		<div class="card m-b-30">
			<div class="card-body">
				<div>
					<p class="cv1">
						<b class="col-ppd">Event Locations</b>
						<router-link v-bind:to="'/director/projects'" class="mdb float-right text-white">View Projects</router-link>
					</p>
					<div class="mt-2">

						<table class="table table-striped mb-0">
							<tbody>
								<tr>
									<th><b>S/N</b></th>
									<th><b>Address</b></th>
									<th><b>Time</b></th>
									<th><b>Date</b></th>
									<th><b>Action</b></th>
								</tr>
							</tbody>
							<tbody>
								<tr v-for="(applicant, index) in eventApplied">
									<td>{{index + 1}}</td>
									<td>{{applicant.address}}</td>
									<td>{{applicant.time}}</td>
									<td>{{applicant.date | moment().format("DD MMM YYYY")}}</td>
									<td>
										<router-link v-bind:to="'/project/invitedLists/'+applicant.id" class="btn btn-outline-success btn-smaller">View Applicants</router-link>
									</td>
								</tr>
							</tbody>
						</table>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import VueStars from 'vue-stars';
	import axios from 'axios';
	import Loader from '../template/loader';
	export default {
		name: 'viewupload',
		data() {
			return {
				eventData: '',
				loading: true,
				token: '',
				userRoleID: '',
				formLoading: '',
				eventApplied: '',
				roleID: '',
				link: '',
				timeForm: '2018-10-03 15:23:44',
				siteUrl: 'https://api.cast.i.ng/',
			};
		},
		components: {
			loader: Loader,
			VueStars: VueStars,
		},
		mounted() {
			let eventid = this.$route.params.id;

			this.token = JSON.parse(localStorage.getItem('token'));
			console.log(this.token);

			var config = {
				headers: {
					'Access-Control-Allow-Origin': '*'
				},
			};

			let userID = JSON.parse(localStorage.getItem('token'));

			axios({
				method: 'GET',
				url: 'https://api.cast.i.ng/projectrole/invited/' + eventid,
				config
			}).then(
				result => {
					this.eventApplied = result.data.event_list;
					
				},
				error => {
					console.log('API CALL FAILED');
					console.error(error);
				}
			);



			this.loading = true;
			axios.get('https://jsonplaceholder.typicode.com/todos/1').then(
				response => {
					this.loading = false;
					console.log('Page Changes');
				},
				error => {
					this.loading = false;
					console.log('Page Error');
				}
			);
		},
		methods: {},
	};
</script>

<style>
	.form-loader {
		width: 22px;
	}

	.success {
		color: #155724;
		background-color: #d4edda;
		border-color: #c3e6cb;
	}

	.danger {
		color: #721c24;
		background-color: #f8d7da;
		border-color: #f5c6cb;
	}

	.btn-ppd:hover {
		background-color: #3f0047 !important;
		color: white !important;
	}
	.btn-smaller{
		font-size: 12px;
	}
</style>