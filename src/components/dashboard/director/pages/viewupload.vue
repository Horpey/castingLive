<template>
	<div>
		<loader v-if="loading" />
		<div class="card m-b-30">
			<div class="card-body">
				<div>
					<p class="cv1">
						<b class="col-ppd">{{uploadData.data.user_name}}</b> Uploads
						<span style="float: right">
							<b class="col-ppd">{{uploadData.data.project_name}}</b>
						</span>
					</p>
					<div class="mt-2">

						<table class="table table-striped mb-0">
							<tbody>
								<tr>
									<th><b>Type</b></th>
									<th><b>Date Uploaded</b></th>
									<th><b>Media</b></th>
									<th><b>Action</b></th>
								</tr>
							</tbody>
							<tbody>
								<tr v-for="upload in uploadData.data.list">
									<td class="text-capitalize">{{upload.type}}</td>
									<td>{{upload.date | moment().format("DD MMM YYYY")}}</td>
									<td>
										<router-link v-if="upload.type === 'video' || upload.type === 'Video'" v-bind:to="'/project/previewVideo/'+upload.filename">
		                                    <span class="fa fa-film"></span>
		                                </router-link>

		                                <router-link v-if="upload.type === 'audio' || upload.type === 'Audio'" v-bind:to="'/project/previewVideo/'+upload.filename">
		                                    <span class="fa fa-volume-up"></span>
		                                </router-link>
									</td>
									<td>
										<router-link class="btn btn-xs btn-outline-success" v-bind:to="'/project/previewVideo/'+upload.filename">
		                                    View
		                                </router-link>
										<button class="btn btn-xs btn-outline-warning">Request for Video</button>
									</td>
								</tr>
								<!-- <tr v-for="upload in uploadData.data.list">
									<td></td>
									<td>{{upload.date | moment().format("DD MMM YYYY")}}</td>
									<td>
										<a :href="upload.media" class="btn btn-outline-success btn-sm" target="_blank">View</a>
									</td>
								</tr> -->
							</tbody>
						</table>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	import Loader from '../template/loader';
	export default {
		name: 'viewupload',
		data() {
			return {
				loading: true,
				token: '',
				userRoleID: '',
				formLoading: '',
				uploadData: '',
				roleID: '',
				link: '',
				timeForm: '2018-10-03 15:23:44',
				siteUrl: 'https://api.cast.i.ng/',
			};
		},
		components: {
			loader: Loader,
		},
		mounted() {
			let userRoleID = this.$route.params.id;

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
				url: 'https://api.cast.i.ng/projectrole/viewupload/' + userRoleID,
				config
			}).then(
				result => {
					this.uploadData = result;
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
</style>