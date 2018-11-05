<template>
    <div>
		<styles/>
		<loader v-if="loading"/>
        <header class="sub-ban1 clippath" :style="{'background': 'linear-gradient(180deg, #000c, #00000080), url('+ require ('../../assets/images/ban1.jpg') + ')'}">
			<div class="container">
				<div class="row">
					<div class="col-lg-12 mx-auto text-white pt-c2">
						<h4>Workshop</h4>
						<router-link class="text-white" v-bind:to="'/Home'">Home</router-link>
						<i class="fa fa-angle-double-right mr-2 ml-2"></i>
						<small>Workshop</small>
					</div>
				</div>
			</div>
		</header>


		<section class="sec-5">
			<div class="container">
				<div class="row">
					<div class="col-lg-8">
						<h1>This is Workshop</h1>
					</div>
				</div>
			</div>
		</section>
    </div>
</template>

<script>
import axios from 'axios';
import Loader from '../template/loader';
import Styles from '../template/styles';
export default {
	name: 'workshop',
	data() {
		return {
			loading: true,
		};
	},
	components: {
		loader: Loader,
		styles: Styles,
	},
	mounted() {
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
.sub-ban1 {
	min-height: 230px;
}
.clippath {
	background-size: cover;
	-webkit-clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
	clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
}
.blog-img {
	width: 100%;
	height: 193px;
	background-size: cover !important;
	background-position: center !important;
	background-repeat: no-repeat !important;
	margin-bottom: 19px;
}
</style>