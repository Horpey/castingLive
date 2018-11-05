<template>
    <div >
		<styles/>
		<loader v-if="loading"/>
        <header>
			<div id="carouselExampleFade" class="carousel slide carousel-fade bgg" data-ride="carousel">
				<div class="carousel-inner">
					<div class="carousel-item" v-for="(slider, index) in sliderData.list" :class="{ 'active': index === 0 }" >
						<div class="clippath" alt="First slide" :style="{'background': 'linear-gradient(180deg, #0000, #00000080), url('+ slider.image + ')' }">
							<div class="container pt-c">
								<div class="row">
									<div class="col-lg-7 mx-auto text-white text-center">
										
										<h1 class="slider-head text-capitalize" style="font-size: 30px;">{{slider.title}}</h1>
										<h5 class="r-14">{{slider.description}}</h5>
										
										<router-link class="r-btn hvr-sweep-to-left btn btn-bb2 mr-2" v-bind:to="'/Registeractor'">I am an Actor</router-link>

										<router-link class="r-btn hvr-sweep-to-left btn btn-bb2" v-bind:to="'/Registerdirector'">I am a Casting
											Director</router-link>

									</div>
								</div>
							</div>
						</div>
					</div>

				</div>
			</div>
		</header>

<section class="sec1 sec-over">
    <div class="container">
		<div id="carouselExampleIndicators7" class="carousel slide" data-ride="carousel">
			<ol class="carousel-indicators pink-indicator">
				<li v-for="(chair, index) in chairSlider" :class="{ 'active': index === 0 }" data-target="#carouselExampleIndicators7" :data-slide-to="index"></li>
			</ol>
			<div class="carousel-inner">
				<div class="carousel-item min-item" v-for="(chair, index) in chairSlider" :class="{ 'active': index === 0 }">
					<div class="row">
			            <div class="col-lg-7 text-left">
			                <h1 class="display-4 slider-head" style="text-align: left;">{{chair.title}}</h1>
			                <p>
			                  	{{chair.description}}
			                </p>

			                <router-link class="btn btn-trans text-white" v-bind:to="'/Register'">Get Started Now</router-link>
			            </div>
			            <div class="col-lg-5 wow slideInRight d-none d-sm-block d-sm-none d-md-block" data-wow-duration="2s"
			                data-wow-offset="10">
			                <img :src="chair.image" class="img-fluid imgv">
			            </div>
			        </div>
				</div>
			</div>
		</div>
	</div>
</section>



<section class="sec5">
	<div class="container">
		<div id="carouselExampleIndicators2" class="carousel slide" data-ride="carousel">
			<ol class="carousel-indicators">
				<li v-for="(featured, index) in featured" :class="{ 'active': index === 0 }" data-target="#carouselExampleIndicators2" :data-slide-to="index"></li>
			</ol>
			<div class="carousel-inner">
				<div class="carousel-item" v-for="(featured, index) in featuredProjects" :class="{ 'active': index === 0 }">
					<div class="row">
						<div class="col-md-4">
							<img class="img-fluid slider-img float-left mr-4 imgcv img-responsive" :src="siteUrl + featured.project_image" alt="">
						</div>
						<div class="col-md-8">
							<h1 class="slider-head text-left">	{{featured.project_title}}</h1>
							<span v-html="featured.project_description"></span>
							<button type="button" class="btn btn-trans">Read More</button>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- <section class="sec5">
	<div class="container">
		<div class="myslid">
			<div v-for="featured in homeData.data.featured_projects">
				<p>
					<img class="img-fluid slider-img float-left mr-4 imgcv" :src="siteUrl + featured.project_image" alt="">
					<h1 class="slider-head text-left">	{{featured.project_title}}</h1>

					<span v-html="featured.project_description"></span>
				</p>
				<button type="button" class="btn btn-trans">Read More</button>
			</div>
		</div>
	</div>
</section> -->

	<div class="container-fluid p-0">

		<div class="my-4" align="center">
			<small class="col-g r-small">CASTING BEST TALENT</small>
			<h1 class="col-p slider-head">Featured Actors
				<div class="uline"></div>
			</h1>
		</div>



		<div class="row no-gutters">
			<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 hover-grid" v-for="actors in featuredActors" >
				<div class="hovereffect">
					<div class="overlay bggdd" :style="{'background': 'linear-gradient(rgba(63, 0, 72, 0.4),rgba(63, 0, 72, 0.4)), url('+ siteUrl + actors.user_image + ')'}">
						<h2 class="text-trans-none"> 
							{{actors.user_firstname}} {{actors.user_lastname}}
							<br>
						</h2>
						<a class="info text-trans-none">
							<small>{{actors.user_description}}
							</small>
						</a>
					</div>
				</div>
			</div>	
		</div>
	</div>


	<section class="sec">
		<div class="container p-0">
			<div class="row">
				<div class="col-lg-4 wow slideInLeft d-none d-sm-block d-sm-none d-md-block text-right" data-wow-duration="2s" data-wow-offset="10">
					<img src="../../assets/images/board3.png" style="margin-top: 37px;" class="img-fluid">
				</div>
				<div class="col-lg-8">
					<div class="wrd r-wrd" style="padding: 10px 80px 80px 0;">
						<h1 class="col-p slider-head hire-the text-left">Hire the Best Casting Talent</h1>
						<!-- <h1>Loading is {{loading}}</h1> -->
						<ul>
							<li v-for="listFeat in listfeats">
								<p style="margin-bottom: 7px; font-size: 18px;">
									<b>{{listFeat}}</b>
								</p>
							</li>
						</ul>

						
					</div>
				</div>
			</div>
		</div>
	</section>
    <section>
		<div class="container-fluid p-0">
		


			<div class="row no-gutters text-center">
				<div class="col-sm-4 col1 r-color-grid">
					<label class="cbox wow fadeIn" data-wow-duration="2s" data-wow-offset="10">
						<i class="fa fa-4x fa-laptop"></i>
					</label>
					<h3>Create Your Profile</h3>
					<p class="mb-0">Create your account in minutes and update your profile.</p>

				</div>
				<div class="col-sm-4 col2 r-color-grid">
					<label class="cbox wow fadeIn" data-wow-duration="3s" data-wow-offset="10">
						<i class="fa fa-4x fa-users"></i>
					</label>
					<h3>Get Countless Casting Calls</h3>
					<p class="mb-0">Upload your reels and resume and start getting casting calls.</p>

				</div>
				<div class="col-sm-4 col3 r-color-grid">
					<label class="cbox wow fadeIn" data-wow-duration="4s" data-wow-offset="10">
						<i class="fa fa-4x fa-list-alt"></i>
					</label>
					<h3>Discover & Hire Talents</h3>
					<p class="mb-0">View actors headshots and resume. Make your selection process easy.</p>

				</div>
			</div>
		</div>
	</section>


	<section class="sec3 r-sec3">
		<div class="container">
			<div class="row">
				<div class="col-lg-8 mx-auto text-white text-left">
					<h1 class="slider-head text-left">What is Casting all about?</h1>
					<p>
						<a class="text-white" href="https://cast.i.ng">www.cast.i.ng</a> is Nigeria’s Premium online end-to-end audition and casting audition platform that answers to the cry of actors and casting directors alike. Born out of the need to replace the crazy audition process that we have in Nigeria today.  We also boast in the ability of our team to represent you as agents or managers. 
					</p>
					<button type="button" class="btn btn-trans">
						<router-link class="text-white" v-bind:to="'/About'">Read More</router-link>
						</button>
				</div>
				<div class="col-lg-4">
					<img class="r-pink-logo" src="../../assets/images/lgm1.png" width="">
				</div>
			</div>
		</div>
	</section>



	
<section class="sec6 r-sec6">
	<div class="container">
		<div id="carouselExampleIndicators3" class="carousel slide" data-ride="carousel" >
			<ol class="carousel-indicators">
				<li v-for="(testimonial, index) in featuredTesti" :class="{ 'active': index === 0 }" data-target="#carouselExampleIndicators3" :data-slide-to="index"></li>
			</ol>
			<div class="carousel-inner">
				<div class="carousel-item" v-for="(testimonial, index) in featuredTesti" :class="{ 'active': index === 0 }">
					<div class="row">
						<div class="col-md-6" style="padding:50px 30px;">
							<img class="quote-mark" src="../../assets/images/quotes-1.png" alt="">
							<h2 class="r-slider-h2">
								<span v-html="testimonial.testimonial_content"></span>
							</h2>
							<img :src="siteUrl + testimonial.testimonial_image" class="rounded-circle float-left mr-2" width="70" height="70" />
							<b class="col-o">{{testimonial.testimonial_name}}</b>
							<br> {{testimonial.testimonial_role}}
						</div>

						<div class="col-md-5">
							<iframe class="embed-responsive-item rounded" width="500" height="350" :src="videoUrl + testimonial.testimonial_video" frameborder="0"
								allowfullscreen></iframe>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>



    </div>
</template>

<script>
import axios from 'axios';

// import homeService from '../../services/homeService'

import Loader from '../template/loader';
import Styles from '../template/styles';

export default {
	name: 'home',
	props: ['message'],
	data() {
		return {
			isActive: true,
			loading: true,
			homeData: {},
			featured: {},
			featuredTesti: {},
			featuredProjects: {},
			featuredActors: {},
			sliderData: {},
			chairSlider: {},
			listfeats: ['Unlimited Headshots',
						'Unlimited Video reels',
						'Unlimited Audio reels',
						'Apply for auditions remotely by one click',
						'Share Online resume/portfolio on your social media',
						'Send Online resume as PDF (e-Size Cards)',
						'Email/WhatsApp reminders of your Audition',
						'Talent Representations - Agency/management', 
						'Access to monthly Actors workshop',
						'Access to Quarterly Actors Hangout' ],
			siteUrl: "https://api.cast.i.ng/",
			videoUrl: "https://www.youtube.com/embed/"
		};
	},
	components: {
		loader: Loader,
		styles: Styles,
	},
	mounted(){
		this.loadingTxt = true
		// location.reload(true);
		if (localStorage.getItem('reloaded')) {
	        // The page was just reloaded. Clear the value from local storage
	        // so that it will reload the next time this page is visited.
	        localStorage.removeItem('reloaded');
	    } else {
	        // Set a flag so that we know not to reload the page twice.
	        localStorage.setItem('reloaded', '1');
	        location.reload(true);
	    }

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

		var config = {
			headers: {'Access-Control-Allow-Origin': '*'}
		};


		axios({ method: "GET", "url": "https://api.cast.i.ng/slider/homepageslider", config }).then(result => {
			this.loading = false;
            this.sliderData = result;
            this.sliderData.list = result.data.list;

        }, error => {
			this.loading = false;
            console.error(error);
        });

        axios({ method: "GET", "url": "https://api.cast.i.ng/slider/chairslider", config }).then(result => {
			this.loading = false;
            // this.chairSlider = result;
            this.chairSlider = result.data.list;

        }, error => {
			this.loading = false;
            console.error(error);
        });
		

        axios({ method: "GET", "url": "https://api.cast.i.ng", config }).then(result => {
			this.loading = false;
            this.featuredProjects = result.data.featured_projects;
            this.featuredActors = result.data.featured_actors
            this.featuredTesti = result.data.featured_testimonial
        }, error => {
			this.loading = false;
            console.error(error);
        });
	}	
};
</script>

<style>
.clippath {
	background-size: cover;
	-webkit-clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
	clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
}
.bgg {
	background-color: #e7077d;
}

.text-trans-none{
	text-transform: none!important;
}

.bggdd{
	background-size: cover!important;
    background-position: center!important;
    background-repeat: no-repeat!important;
}
.carousel-indicators{
	bottom: -40px!important;
}
.carousel-indicators li{
	width: 10px!important;
    height: 10px!important;
    border-radius: 100%;
	background-color: rgba(121, 121, 121, 0.5)!important;
}
.carousel-item {
    border-bottom: 0px!important;
    background-size: cover!important;
    background-repeat: no-repeat!important;
}
.carousel-item div{
	background-repeat: no-repeat!important;
	background-size: cover!important;
}
.min-item{
	max-height: 458px;
    padding: 100px 0 10px 0;
    color: #fff;
    background-color: #e7077d;
    overflow-x: hidden;
    overflow-y: hidden;
}
.sec-over{
    overflow-y: hidden;
    padding-top: 0px!important;
}
.pink-indicator{
	bottom: -3px!important;
}
.pink-indicator li{
	    background-color: white!important;
}
</style>