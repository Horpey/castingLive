<template>
    <div>
        <loader v-if="loading"/>
        <header class="sub-ban clippath" :style="{'background': 'linear-gradient(180deg, #000c, #00000080), url('+ require ('../../assets/images/background.jpg') + ')'}">
    <div class="container about-headd" style="padding-top: 175px;">
        <div class="row">
            <div class="col-lg-7 mx-auto text-white text-center">
                <h2>The best talents in the land get hired here</h2>
                <p>We provide the the most convenient place for talented actors and the casting Directors who need
                    their services
                    to meet, and get work started.</p>
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


<section class="line">
    <div class="container-fluid p-0">

        <div class="row no-gutters text-center">
            <div class="col-sm-4 col1 r-color-grid">
                <router-link class="text-white" v-bind:to="'/register'">
                    <label class="cbox wow fadeIn" data-wow-duration="2s" data-wow-offset="10">
                    <i class="fa fa-4x fa-laptop"></i>
                    </label>
                    <h3>Create Your Profile</h3>
                    <p class="mb-0">Create your account in minutes and update your profile.</p>
                </router-link>
            </div>
            <div class="col-sm-4 col2 r-color-grid">
                <router-link class="text-white" v-bind:to="'/register'">
                    <label class="cbox wow fadeIn" data-wow-duration="3s" data-wow-offset="10">
                        <i class="fa fa-4x fa-users"></i>
                    </label>
                    <h3>Get Countless Casting Calls</h3>
                    <p class="mb-0">Upload your reels and resume and start getting casting calls.</p>
                </router-link>
            </div>
            <div class="col-sm-4 col3 r-color-grid">
                <router-link class="text-white" v-bind:to="'/register'">
                    <label class="cbox wow fadeIn" data-wow-duration="4s" data-wow-offset="10">
                        <i class="fa fa-4x fa-list-alt"></i>
                    </label>
                    <h3>Discover & Hire Talents</h3>
                    <p class="mb-0">View actors headshots and resume. Make your selection process easy.</p>
                </router-link>

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
	name: 'about',
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

		axios.get('https://jsonplaceholder.typicode.com/todos/1').then(
			response => {
				this.loading = false;
			},
			error => {
				this.loading = false;
				console.log('Page Error');
			}
		);
	},
    head: {
      title: {
        inner: 'About'
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
.sub-ban {
	min-height: 400px;
}
.clippath {
	background-size: cover;
	-webkit-clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
	clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
}
.btn-trans{
        background: #e7077d;
    margin-bottom: 100px;
}
</style>