<template>
    <div>
        <loader v-if="loading"/>
        <div class="card m-b-30">
            <div class="card-body">
                <h3>Edit Project
                    <router-link class="mdb role-add float-right" v-bind:to="'/director/projects'">View Projects</router-link>

                </h3>
                <hr>
                <div class=" m-b-30">
                    <div class="container">
                        <div class="row">

                        	<form class="msform mt-2" @submit.prevent="editProject">
			                    <div class="add-project-group">
			                        <b>Project Title:</b>
			                        <input class="mb-2" type="text" placeholder="Project Title" v-model="title" required="">
			                        <b>Project type</b>
			                        <select class="mb-2" v-model="type_id" required="">
			                            <option value="">--Select--</option>
			                            <option v-for="projectType in projectTypes.data.list" :value="projectType.id">{{projectType.title}}</option>
			                        </select>

			                        <b>Project description</b>
			                        <textarea class="mb-2" col="10" v-model="description" required=""></textarea>
			                        <div class="row">
			                            <div class="col-lg-6">
			                                <b>Minimum Pay</b>
			                                <input class="mb-2" type="number" placeholder="Minimum Pay" v-model="payrange_min"
			                                    required="">
			                            </div>

			                            <div class="col-lg-6">
			                                <b>Maximum Pay</b>
			                                <input class="mb-2" type="number" placeholder="Maximum Pay" v-model="payrange_max"
			                                    required="">
			                            </div>
			                        </div>

			                        <div class="row">
			                            <div class="col-lg-6">
			                                <b>City of audition:</b>
			                                <input class="mb-2" type="text" placeholder="City of audition" v-model="project_city"
			                                    required="">
			                            </div>

			                            <div class="col-lg-6">
			                                <b>City of shoot:</b>
			                                <input class="mb-2" type="text" placeholder="City of shoot" v-model="shoot_city"
			                                    required="">
			                            </div>
			                        </div>

			                        <div class="row">
			                            <div class="col-lg-6">
			                                <b>Speculated Date of shoot:</b>
			                                <input class="mb-2 inputdatepicker" type="date" placeholder="Speculated Date of shoot"
			                                    v-model="shoot_date" required="">
			                            </div>
			                            <div class="col-lg-6">
			                                <b>Date to take down ad:</b>
			                                <input class="mb-2 inputdatepicker" type="date" placeholder="Date to take down ad"
			                                    v-model="expire_date" required="">
			                            </div>
			                        </div>

			                        <b>How did you hear about us?</b>
			                        <textarea class="mb-2" col="10" v-model="hearabout"></textarea>

			                        <b>Project Image</b>
			                        <input class="" type="file" @change="processFile($event)" accept="image/*">
			                    </div>

			                    <div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }"
			                        v-if="error">{{
			                        error }}</div>

			                    <div class="" style="margin-top: 15px;">
			                        <button type="submit" class="btn btn-ppd wd">
			                            <img v-if="formLoading" class="form-loader" src="../../../../assets/images/white-loader.svg"
			                                alt="Loader" />
			                            <span v-if="!formLoading">Save Project</span>
			                        </button>
			                    </div>
			                </form>


                            <!-- <div class="cv2 mt-2" v-for="role in detailsData.data.list">
                                <div class="col-md-12 mt-2">
                                    <h2>
                                        {{role.role_name}}
                                    </h2>
                                    <p>
                                        <b class="col-ppd">Description</b>: {{role.description}}</p>
                                    <p>
                                        <b class="col-ppd">Applicant</b>: {{role.applicants}}</p>
                                    <p>

                                        <router-link class="btn btn-primary btn-sm border-0" v-bind:to="'/project/editRole/'+role.id">Edit Role</router-link>

                                        <router-link class="btn btn-ppd btn-sm border-0" v-bind:to="'/project/applicants/'+role.id">View Applicants</router-link>

                                    </p>
                                </div>
                            </div> -->

                        </div>
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
	name: 'edit',
	data() {
		return {
			loading: true,
            error: false,
            formLoading: '',
            projectTypes: '',
            token: '',
            title: '',
            type_id: '',
            description: '',
            payrange_min: '',
            payrange_max: '',
            project_city: '',
            shoot_city: '',
            shoot_date: '',
            expire_date: '',
            hearabout: '',
            image: '',
            img: '',
            siteUrl: "https://api.cast.i.ng/",
		};
	},
	components: {
		loader: Loader,
	},
	mounted() {
		let projectID = this.$route.params.id;

		this.detailID = projectID;

		this.token = JSON.parse(localStorage.getItem('token'));

		var config = {
			headers: { 'Access-Control-Allow-Origin': '*' },
		};

		let userID = JSON.parse(localStorage.getItem('token'));
        axios({
            method: "GET",
            "url": 'https://api.cast.i.ng/project/' + projectID,
            config
        }).then(result => {
        	console.log(result.data);
            this.editProjectData = result.data;
            this.title = this.editProjectData.title;
            this.type_id = this.editProjectData.type_id;
            this.description = this.editProjectData.description;
            this.payrange_min = this.editProjectData.payrange_min;
            this.payrange_max = this.editProjectData.payrange_max;
            this.project_city = this.editProjectData.project_city;
            this.shoot_city = this.editProjectData.project_shootcity;
            this.shoot_date = this.editProjectData.project_shootdate;
            this.expire_date = this.editProjectData.project_expire;
            this.hearabout = this.editProjectData.project_hearabout;
            this.title = this.editProjectData.title;


        }, error => {

            console.log('API CALL FAILED');
            console.error(error);
        });

		axios({ method: 'GET', url: 'https://api.cast.i.ng/director/projectroles/' + projectID, config }).then(
			result => {
				this.detailsData = result;
			},
			error => {
				console.log('API CALL FAILED');
				console.error(error);
			}
		);

		// Get Project Types
        axios({
            method: "GET",
            "url": 'https://api.cast.i.ng/projecttypes',
            config
        }).then(result => {
            this.loading = false;
            this.projectTypes = result;
        }, error => {
            this.loading = false;
            console.log('API CALL FAILED');
            console.error(error);
        });

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
		processFile(event) {
            event.target.files[0]
            this.img = event.target.files[0];
        },
		editProject(){
			let form = new FormData();

            form.append('title', this.title);
            form.append('type_id', this.type_id);
            form.append('description', this.description);
            form.append('payrange_min', this.payrange_min);
            form.append('payrange_max', this.payrange_max);
            form.append('project_city', this.project_city);
            form.append('shoot_city', this.shoot_city);
            form.append('shoot_date', this.shoot_date);
            form.append('expire_date', this.expire_date);
            form.append('hearabout', this.hearabout);
            form.append('image', this.img);

            this.formLoading = true;

            let userID = JSON.parse(localStorage.getItem('token'));
            let projectID = this.$route.params.id;

            const API_URL = process.env.API_URL || 'https://api.cast.i.ng'

            axios.post(API_URL + '/project/edit/' + projectID, form).then(result => {

                console.log(userID);
                this.formLoading = false;

                console.log(result.data)

                this.error = result.data.status_msg;
                this.status = result.data.status;

                // this.$router.replace(this.$route.query.redirect || '/director/profile')

            }, error => {
                this.formLoading = false;
                console.error(error);
                console.log('API CALL FAILED')
                this.error = "Failed to Edit Project";
            });
		}
	}
};
</script>

<style>
    .msform input[type='url'],
    .msform input[type='number'],
    .msform input[type='date'] {
        padding: 6px;
        border: 1px solid #ccc;
        border-radius: 3px;
        width: 100%;
        box-sizing: border-box;
        color: #2c3e50;
        font-size: 13px;
    }
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