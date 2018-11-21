<template>
    <div>
        <loader v-if="loading"/>
        <div class="card m-b-30">
            <div class="card-body">
                <h3>{{detailsData.data.project_title}} - Project Roles

                	<a style="margin-left: 10px;" target="_blank" :href="'https://api.cast.i.ng/recordprovideo/'+ projectidd" class="mdb role-add float-right">Add Video Intro</a>

                    <router-link class="mdb role-add float-right" v-bind:to="'/project/addRole/'+detailID">Add Role</router-link>

                </h3>
                <hr>
                <div class=" m-b-30">
                    <div class="">
                        <div class="row">

                            <div class="cv2 mt-2" v-for="role in detailsData.data.list">
                                <div class="col-md-12 mt-2">
                                    <h2>
                                        {{role.role_name}}

                                         <div class="dropdown">
                                            <button class="float-right btn btn-ppd btn-sm dropdown-toggle" type="button" data-toggle="dropdown" style="bottom: 40px;">
                                                Settings
                                                <span class="caret"></span>
                                            </button>
                                            <div id="pos">
                                                <ul class="dropdown-menu">
                                                    <li>
                                                        <router-link class="dropdown-item" v-bind:to="'/project/editRole/'+role.id">Edit Role</router-link>
                                                    </li>

                                                    <li>

                                                        <router-link class="dropdown-item" v-bind:to="'/project/applicants/'+role.id">View Applicant</router-link>
                                                    </li>

                                                    <li>

                                                        <a target="_blank" :href="'https://api.cast.i.ng/recordprovideo/'+ role.id +'?t=r'" class="dropdown-item">Add Video Intro</a>
                                                    </li>

                                                </ul>
                                            </div>
                                        </div>

                                    </h2>
                                    <p>
                                        <b class="col-ppd">Description</b>: <span class="desc-limit">{{role.description}} </span></p>
                                    <!-- <p>
                                        <b class="col-ppd">Applicant</b>: {{role.applicants}}</p>
                                    <p>

                                        <router-link class="btn btn-primary btn-sm border-0" v-bind:to="'/project/editRole/'+role.id">Edit Role</router-link>

                                        <router-link class="btn btn-ppd btn-sm border-0" v-bind:to="'/project/applicants/'+role.id">View Applicants</router-link>

                                    </p> -->
                                </div>
                            </div>

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
	name: 'details',
	data() {
		return {
			loading: true,
			detailsData: '',
			token: '',
			projectidd: '',
			detailID: '',
			siteUrl: 'https://api.cast.i.ng/',
		};
	},
	components: {
		loader: Loader,
	},
	mounted() {
		let projectID = this.$route.params.id;

		this.projectidd = this.$route.params.id;

		this.detailID = projectID;

		this.token = JSON.parse(localStorage.getItem('token'));
		console.log(this.token);

		var config = {
			headers: { 'Access-Control-Allow-Origin': '*' },
		};

		let userID = JSON.parse(localStorage.getItem('token'));

		axios({ method: 'GET', url: 'https://api.cast.i.ng/director/projectroles/' + projectID, config }).then(
			result => {
				this.detailsData = result;
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
};
</script>

<style>
.desc-limit {
	overflow: hidden;
	text-overflow: ellipsis;
	display: -webkit-box;
	line-height: 19px;
	max-height: 97px;
	    margin-top: 16px;
	-webkit-line-clamp: 3;
	-webkit-box-orient: vertical;
}
</style>