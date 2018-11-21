<template>
    <div>
		<loader v-if="loading"/>
        <header class="sub-ban1 clippath" :style="{'background': 'linear-gradient(180deg, #000c, #00000080), url('+ require ('../../assets/images/background.jpg') + ')'}">
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

		<section class="sec-1 line r-sec-1">
		    <div class="container">
		        <div class="row">
		            <div class="col-lg-4 wow slideInRight" data-wow-duration="2s" data-wow-offset="10">
		                <img  src="../../assets/images/castb.png" class="img-fluid text-center pt-3 my-auto"style="width:100%">
		            </div>
		            <div class="col-lg-8 text-left  wow slideInLeft" data-wow-duration="2s" data-wow-offset="10">
		                <h1 class="col-p slider-head text-left">{{aboutTitle}}</h1>
		                <div v-html="aboutData"></div>
		                <router-link class="btn btn-trans" v-bind:to="'/register'">Get Started Now</router-link> 
		            </div>
		            
		        </div>
		    </div>
		</section>


    </div>
</template>

<script>
import axios from 'axios';
import Loader from '../template/loader';
export default {
	name: 'workshop',
	data() {
		return {
			loading: true,
			aboutData: '',
            aboutTitle: '',
		};
	},
	components: {
		loader: Loader,
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

		axios.get('https://api.cast.i.ng/getpage/about-us').then(
            response => {
                this.aboutData = response.data.page_content;
                this.aboutTitle = response.data.page_title;
            },
            error => {
                this.loading = false;
                console.log('Page Error');
            }
        );

	},
	head: {
	  title: {
	    inner: 'Workshop'
	  },
	  // Meta tags
	  meta: [
	    { name: 'application-name', content: 'Casting' },
	    { name: 'description', content: 'Nigeria’s Number 1 premium casting website, for real actors by real casting directors. Powered by technology, with the aim of ease, efficiency and affordability.', id: 'desc' }, // id to replace intead of create element
	    // ...
	    // Twitter
	    { name: 'twitter:title', content: 'Casting' },
	    // with shorthand
	    { n: 'twitter:description', c: 'Nigeria’s Number 1 premium casting website, for real actors by real casting directors. Powered by technology, with the aim of ease, efficiency and affordability.'},
	    // ...
	    // Facebook / Open Graph
	    { property: 'fb:app_id', content: '123456789' },
	    { property: 'og:title', content: 'Casting' },
	    // with shorthand
	    { p: 'og:image', c: 'https://cast.i.ng/static/img/icons/favicon-32x32.png' },
	    // ...
	  ]
	}
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
.btn-trans{
        background: #e7077d;
    margin-bottom: 100px;
}
</style>