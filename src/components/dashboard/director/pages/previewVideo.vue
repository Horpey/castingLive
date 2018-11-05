<template>
	<div>
		<loader v-if="loading" />
		<div class="card m-b-30">
			<div class="card-body">
				<div>
					<p class="cv1">
						<b class="col-ppd">Preview Video</b>
						 <router-link v-bind:to="'/director/projects'" class="mdb float-right text-white">View Projects
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
		name: 'previewVideo',
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
			let videoID = this.$route.params.id;
			this.videoUrl = 'https://castcdn.tk/video/'+videoID+'.mp4';
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