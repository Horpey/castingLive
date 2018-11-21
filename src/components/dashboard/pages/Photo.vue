<template>
    <div>
        <loader v-if="loading"/>
        <div class="card m-b-30">
            <div class="card-body">
                <div class="row">
                	<div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="error">{{
								error }}</div>	
                    <p class="cv1">
                        <b>HEADSHOT PHOTOS</b>
                        <router-link class="mdb float-right text-white" v-bind:to="'/dashboard/addMedia'">Add Photos</router-link>
                    </p>		
                    
                    <div class="container">
                    	<div class="row">
	                    	<div class="col-md-3 p-1" v-for="photo in headshot">
		                        <a target="_blank" :href="siteUrl + photo.image" data-fancybox="gallery">
		                            <img class="rounded mx-auto d-block img-fluid" alt="200x200" :src="siteUrl + photo.image" data-holder-rendered="true" /> 
		                        </a>
		                        <button v-on:click="deleteImage(photo.id)" class="mv"><i class="fa fa-trash-o"></i> Delete</button>
		                    </div>
	                   	</div>		
                    </div>
                    	
                    <p class="cv1">
                        <b>BEHIND THE SCENE PHOTOS</b>
                        <router-link class="mdb float-right text-white" v-bind:to="'/dashboard/addMedia'">Add Photos</router-link>
                    </p>	

                    <div class="container">
                    	<div class="row">
	                    	<div class="col-md-3 p-1" v-for="photo in scene">
		                        <a target="_blank" :href="siteUrl + photo.image" data-fancybox="gallery">
		                            <img class="rounded mx-auto d-block img-fluid" alt="200x200" :src="siteUrl + photo.image" data-holder-rendered="true" /> 
		                        </a>
		                        <button v-on:click="deleteImage(photo.id)" class="mv"><i class="fa fa-trash-o"></i> Delete</button>
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
	name: 'photo',
	data() {
		return {
			loading: true,
			photoData: '',
			error: '',
			token: '',
			headshot: [],
			scene: [],
			siteUrl: 'https://api.cast.i.ng/',
		};
	},
	components: {
		loader: Loader,
	},
	methods: {
		deleteImage(imageID) {

			var result = confirm("Are you sure?");
			if (result) {
			   // confirm('Are you sure?');
				var config = {
					headers: { 'Access-Control-Allow-Origin': '*' },
				};

				axios({ method: 'GET', url: 'https://api.cast.i.ng/delete/album_item/' + imageID, config }).then(
					result => {
						this.loading = false;
						this.error = result.data.status_msg;
						location.reload();

						// this.$router.replace(this.$route.query.redirect || '/dashboard/profile');
					},
					error => {
						this.loading = false;
						console.log('API CALL FAILED');
						// this.$router.replace(this.$route.query.redirect || '/dashboard/profile');
						console.error(error);
					}
				);
			}
			
		},
	},
	mounted() {
		this.token = JSON.parse(localStorage.getItem('token'));
		console.log(this.token);

		this.loading = true;

		var config = {
			headers: { 'Access-Control-Allow-Origin': '*' },
		};

		let userID = JSON.parse(localStorage.getItem('token'));
		// console.log(userID);

		axios({ method: 'GET', url: 'https://api.cast.i.ng/myphoto/' + userID, config }).then(
			result => {
				this.loading = false;
				// this.photoData = result;
				this.headshot = result.data.headshot_list;
				this.scene = result.data.scene_list;
			},
			error => {
				this.loading = false;
				console.log('API CALL FAILED');
				console.error(error);
			}
		);
	},
};
</script>

<style>
.mv{
    position: relative;
    bottom: 42px;
    left: 9px;
    background-color: white;
    padding: 4px;
    color: #850000;
    border: 0px;
    cursor: pointer;
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
</style>