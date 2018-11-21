<template>
	<div>
		<loader v-if="loading" />
		<div class="card m-b-30">
			<div class="card-body">
				<div>
					<p class="cv1">
						<b class="col-ppd">Video Intro</b>
						 <router-link v-bind:to="'/dashboard/auditions'" class="mdb float-right text-white">View Auditions
                                </router-link>
					</p>
					<div style="text-align: center;">
						<video style="width: 80%;" height="350" controls>
							<source :src="videoUrl">
						  <!-- <source src="http://techslides.com/demos/sample-videos/small.mp4" type="video/mp4"> -->
						  <!-- <source src="movie.ogg" type="video/ogg"> -->
						  Your browser does not support the video tag.
						</video>
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
		name: 'introVideo',
		data() {
			return {
				loading: true,
				token: '',
				userRoleID: '',
				formLoading: '',
				videoUrl: '',
				siteUrl: 'https://api.cast.i.ng/',
			};
		},
		components: {
			loader: Loader,
		},
		mounted() {
			// let videoID = JSON.parse(localStorage.getItem('introVid'));
			this.videoUrl = localStorage.getItem('introVid');;
			console.log(this.videoUrl);
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
</style>