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

					<div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="status || statusFalse">{{ error }}</div>

					<div class="applicantFilter text-right">

                        <a v-if="applicantChecked" style="margin-bottom: 15px;" class="btn btn-filled btn-xs btn-success" v-on:click="acceptApplicant">
                            Accept
                        </a>

                        <a v-if="applicantChecked" style="margin-bottom: 15px;" class="btn btn-filled btn-xs btn-danger" v-on:click="declineApplicant">
                            Decline
                        </a>
                        
                    </div>

					<div class="mt-2">
						<table class="table table-striped mb-0">
							<tbody>
								<tr>
									<th>
										<div class="form-check">
		                                    <label class="form-check-label">
		                                        <input type="checkbox" class="form-check-input all-check" @click="selectAll" v-model="allSelected">
		                                        <b> All</b>
		                                    </label>
		                                 </div>
									</th>
									<th><b>Name</b></th>
									<th><b>Rating</b></th>
									<th><b>Time</b></th>
									<th><b>Address</b></th>
									<th><b>Action</b></th>
								</tr>
							</tbody>
							<tbody>
								<tr v-for="(applicant, index) in listApplic">
									<td>
										<div class="form-check">
                                            <label class="form-check-label mb-3">
                                                <input @click="checkforLength" type="checkbox" class="form-check-input all-checked"
                                                    v-model="filterIDs" :value="applicant.user_id">
                                            </label>
                                        </div>
									</td>
									<td>{{applicant.user_name}}</td>
									<td>{{applicant.user_rating}}</td>
									<td>{{applicant.user_time}}</td>
									<td>
										{{applicant.event_address}}
									</td>
									<td>
										<button v-on:click="acceptApply(applicant.user_id)" class="btn btn-filled btn-xs btn-success">Accept</button>
										<button v-on:click="declineApply(applicant.user_id)" class="btn btn-filled btn-xs btn-danger">Decline</button>
<!-- <button v-on:click="deleteJob(feature.id)" class="btn btn-outline-danger btn-sm">Delete</button> -->
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
		name: 'invitedLists',
		data() {
			return {
				eventData: '',
				loading: true,
				allSelected: false,
				applicantChecked: false,
				token: '',
				userRoleID: '',
				filterIDs: [],
				formLoading: '',
				listApplic: '',
				roleID: '',
				link: '',
				error: false,
				status: false,
				statusFalse: false,
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
				url: 'https://api.cast.i.ng/event/invited/' + eventid,
				config
			}).then(
				result => {
					this.listApplic = result.data.list;
					
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
		methods: {
			acceptApply(applyID){
				let form = new FormData();
	            var acceptID = [];
	            let projectID = JSON.parse(localStorage.getItem('projectRoleID'));

	            // console.log(applyID)

	            acceptID.push(applyID);

	            var usersAdd = JSON.stringify(acceptID);

	            console.log(usersAdd + "/" + projectID);

	            form.append('users', usersAdd);
	            form.append('projectrole_id', projectID);

	            this.formLoading = true;

	            const API_URL = process.env.API_URL || 'https://api.cast.i.ng';

	            axios.post(API_URL + '/audition/accept', form).then(
	                result => {
	                    this.formLoading = false;

	                    console.log(result.data.status_msg + result.data.status);

	                    this.error = result.data.status_msg;
	                    this.status = result.data.status;   
	                },
	                error => {
	                    this.formLoading = false;
	                    console.error(error);
	                    this.statusFalse = true;
	                    this.error = 'Failed to Decline Applicant';
	                }
	            );
			},
			declineApply(applyID){
				let form = new FormData();
	            var acceptID = [];
	            let projectID = JSON.parse(localStorage.getItem('projectRoleID'));

	            // console.log(applyID)

	            acceptID.push(applyID);

	            var usersAdd = JSON.stringify(acceptID);

	            console.log(usersAdd + "/" + projectID);

	            form.append('users', usersAdd);
	            form.append('projectrole_id', projectID);

	            this.formLoading = true;

	            const API_URL = process.env.API_URL || 'https://api.cast.i.ng';

	            axios.post(API_URL + '/audition/decline', form).then(
	                result => {
	                    this.formLoading = false;

	                    console.log(result.data.status_msg + result.data.status);

	                    this.error = result.data.status_msg;
	                    this.status = result.data.status;   
	                },
	                error => {
	                    this.formLoading = false;
	                    console.error(error);
	                    this.statusFalse = true;
	                    this.error = 'Failed to Decline Applicant';
	                }
	            );
			},
			selectAll: function() {
	            this.filterIDs = [];

	            if (!this.allSelected) {
	                var filterId = 0;

	                for (filterId in this.listApplic) {
	                    this.filterIDs.push(this.listApplic[filterId].user_id);
	                }
	            }
	        },
	        checkforLength(){
	            if(this.filterIDs.length < -1){
	                this.applicantChecked = false;
	            }else{
	                this.applicantChecked = true;
	            }
	        },
	        acceptApplicant(){
	        	let form = new FormData();

	            var config = {
	                headers: { 'Access-Control-Allow-Origin': '*' },
	            };

	            let userID = JSON.stringify(this.filterIDs);

	            console.log(userID)
	            let projectID = JSON.parse(localStorage.getItem('projectRoleID'));

	            form.append('users', userID);
	            form.append('projectrole_id', projectID);

	            this.formLoading = true;

	            const API_URL = process.env.API_URL || 'https://api.cast.i.ng';

	            axios.post(API_URL + '/audition/accept', form).then(
	                result => {
	                    this.formLoading = false;

	                    console.log(result.data);

	                    this.error = result.data.status_msg;
	                    this.status = result.data.status;   },
	                error => {
	                    this.formLoading = false;
	                    console.error(error);
	                    this.error = 'Failed to Decline Applicant';
	                }
	            );
	        },
	        declineApplicant(){

	            let form = new FormData();

	            var config = {
	                headers: { 'Access-Control-Allow-Origin': '*' },
	            };

	            let userID = JSON.stringify(this.filterIDs);

	            console.log(userID)
	            let projectID = JSON.parse(localStorage.getItem('projectRoleID'));

	            form.append('users', userID);
	            form.append('projectrole_id', projectID);

	            this.formLoading = true;

	            const API_URL = process.env.API_URL || 'https://api.cast.i.ng';

	            axios.post(API_URL + '/audition/decline', form).then(
	                result => {
	                    this.formLoading = false;

	                    console.log(result.data);

	                    this.error = result.data.status_msg;
	                    this.status = result.data.status;   },
	                error => {
	                    this.formLoading = false;
	                    console.error(error);
	                    this.error = 'Failed to Decline Applicant';
	                }
	            );
	        },
		},
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
	
	.applicantFilter {
		padding: 14px 22px 8px;
		background-color: #f3f4f7;
		width: 100%;
		margin-top: 20px;
		border: 1px solid gainsboro;
	}
</style>