<template>
    <div>
        <loader v-if="loading"/>
        <div id="editor"></div>
        <div id="appendImg"></div>
        <div id="capture" class="card m-b-30">
            <div class="card-body">
                <div class="row">
                    <div class="col-md-3">
                        <div class="img-preview" :style="{'background': ' url('+ profileData.data.profile.image + ')' }">
                        </div>

                    </div>
                    <div class="col-md-9">

                        <h4>{{profileData.data.profile.lastname}} {{profileData.data.profile.firstname}}
                        
                        <a v-on:click="pdfGenerate" class="asPDF" style="cursor: pointer;">
                                        <span class="fa fa-file-pdf-o"></span>  Download PDF</a>
                        </h4>
                        
                        <hr>
                        <div class="d-inline">
                            <button class="btn btn-secondary" data-toggle="modal" data-target="#rateApplicant" >
                                Rate Applicant </button>
                        </div>


                        <div class="dropdown d-inline">
                            <button type="button" data-toggle="dropdown" class="btn btn-secondary dropdown-toggle" aria-expanded="false">
                                Share Profile<span class="caret"></span></button>
                            <div id="pos">
                                <ul class="dropdown-menu">
                                    <li>
                                        <vue-goodshare-facebook
                                            :page_url="currentUrl"
                                            title_social="Facebook"
                                            button_design="gradient"
                                            has_icon
                                          ></vue-goodshare-facebook>
                                    </li>
                                    <li>
                                        <vue-goodshare-twitter
                                            :page_url="currentUrl"
                                            title_social="Twitter"
                                            button_design="gradient"
                                            has_icon
                                          ></vue-goodshare-twitter>
                                    </li>
                                    <li>
                                        <vue-goodshare-LinkedIn
                                            :page_url="currentUrl"
                                            title_social="LinkedIn"
                                            button_design="gradient"
                                            has_icon
                                          ></vue-goodshare-LinkedIn>
                                    </li>
                                    <li>
                                        <vue-goodshare-WhatsApp
                                            :page_url="currentUrl"
                                            title_social="WhatsApp"
                                            button_design="gradient"
                                            has_icon
                                          ></vue-goodshare-WhatsApp>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
                <div >
                    <div class="mt-2" >
                        <p class="cv1">
                            <b class="col-ppd">Feature Film</b>
                        </p>
                        <table class="table table-striped mb-0">
                            <tr>
                                <td>
                                    <b>Year</b>
                                </td>
                                <td>
                                    <b>Film</b>
                                </td>
                                <td>
                                    <b>Role</b>
                                </td>
                                <td>
                                    <b>Director</b>
                                </td>
                                <td>
                                    <b>Production Company</b>
                                </td>
                            </tr>

                            <tbody>
                                <tr v-for="feature in profileData.data.featurefilm">
                                    <td>
                                        <i class="fa fa-calendar"></i> {{feature.year}}</td>
                                    <td>{{feature.film}}</td>
                                    <td>{{feature.role}}</td>
                                    <td>{{feature.director}}</td>
                                    <td>{{feature.production_company}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="mt-3">
                        <p class="cv1">
                            <b class="col-ppd">TV Series</b>

                        </p>
                        <table class="table table-striped mb-0">
                            <tr>
                                <td>
                                    <b>Year</b>
                                </td>
                                <td>
                                    <b>Film</b>
                                </td>
                                <td>
                                    <b>Role</b>
                                </td>
                                <td>
                                    <b>Director</b>
                                </td>
                                <td>
                                    <b>Production Company</b>
                                </td>
                            </tr>
                            <tbody>
                                <tr v-for="tv in profileData.data.tvseries">
                                    <td>
                                        <i class="fa fa-calendar"></i> {{tv.year}}</td>
                                    <td>{{tv.film}}</td>
                                    <td>{{tv.role}}</td>
                                    <td>{{tv.director}}</td>
                                    <td>{{tv.production_company}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="mt-3">
                        <p class="cv1">
                            <b class="col-ppd">Web Series</b>
                        </p>
                        <table class="table table-striped mb-0">
                            <tr>
                                <td>
                                    <b>Year</b>
                                </td>
                                <td>
                                    <b>Film</b>
                                </td>
                                <td>
                                    <b>Role</b>
                                </td>
                                <td>
                                    <b>Director</b>
                                </td>
                                <td>
                                    <b>Production Company</b>
                                </td>
                            </tr>
                            <tbody>
                                <tr v-for="web in profileData.data.webseries">
                                    <td>
                                        <i class="fa fa-calendar"></i> {{web.year}}</td>
                                    <td>{{web.film}}</td>
                                    <td>{{web.role}}</td>
                                    <td>{{web.director}}</td>
                                    <td>{{web.production_company}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="mt-3">
                        <p class="cv1">
                            <b class="col-ppd">Theater/Stage Plays</b>
                        </p>

                        <div class="mt-2">
                            <table class="table table-striped mb-0">
                                <tr>
                                    <td>
                                        <b>Year</b>
                                    </td>
                                    <td>
                                        <b>Film</b>
                                    </td>
                                    <td>
                                        <b>Role</b>
                                    </td>
                                    <td>
                                        <b>Director</b>
                                    </td>
                                     <td>
                                        <b>Production Company</b>
                                    </td>
                                </tr>
                                <tbody>
                                    <tr v-for="theater in profileData.data.theater">
                                        <td>
                                            <i class="fa fa-calendar"></i> {{theater.year}}</td>
                                        <td>{{theater.film}}</td>
                                        <td>{{theater.role}}</td>
                                        <td>{{theater.director}}</td>
                                        <td>{{theater.production_company}}</td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                    <div class="mt-3" id="content">
                        <p class="cv1">
                            <b class="col-ppd">Social Handles</b>
                        </p>

                        <a target="_blank" :href="profileData.data.social.facebook">
                            <i class="fa fa-2x fa-facebook-square" style="color:#3b5998;"></i>
                        </a>
                        <a target="_blank" :href="profileData.data.social.twitter">
                            <i class="fa fa-2x fa-twitter-square" style="color:#08a0e9;"></i>
                        </a>
                        <a target="_blank" :href="profileData.data.social.linkedln">
                            <i class="fa fa-2x fa-linkedin-square" style="color:#0077b5;"></i>
                        </a>
                        <a target="_blank" :href="profileData.data.social.instagram">
                            <i class="fa fa-2x fa-instagram" style="color:#da1a42;"></i>
                        </a>
                    </div>
                    <div class="mt-3">
                        <p class="cv1">
                            <b class="col-ppd">Trainings And Education</b>
                        </p>
                        <div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="error">{{ error }}</div>
                        <table class="table table-striped mb-0">

                            <tbody>
                                <tr v-for="education in profileData.data.education">
                                    <td>
                                        <i class="fa fa-calendar"></i> {{education.year}}</td>
                                    <td>{{education.school}}</td>
                                    <td>{{education.certificate}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="mt-3">
                        <p class="cv1">
                            <b class="col-ppd">Photo</b>
                        </p>

                        <div class="row no-gutters mt-2">
                            <div class="col-md-3 p-1" v-for="photo in photoData.data.list">
                                <a :href="siteUrl + photo.image" data-fancybox="gallery">
                                    <img class="rounded mx-auto d-block img-fluid" alt="200x200" :src="siteUrl + photo.image" data-holder-rendered="true" />
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="mt-3">
                        <p class="cv1">
                            <b class="col-ppd">Video</b>

                        </p>


                        <div class="row no-gutters mt-2">
                            <div class="col-md-6 bline" v-for="video in videoData.data.list">
                                <div class="row">
                                    <div class="col-md-6 p-1">
                                         <a data-fancybox="gallery" :href='"https://www.youtube.com/watch?v=_sI_Ps7JSEk"+video.youtube_link'>         
                                            <img class="rounded  mx-auto d-block img-fluid" alt="200x200" :src="video.image" />  
                                        </a>                                            
                                    </div>
                           
                                    <div class="col-md-6">
                                        <p><b>Title:</b>{{video.title}}</p>
                                        <p><b>Year:</b> {{video.year}}</p>
                                        <p><b>Role:</b>{{video.type}}</p>
                                    </div>
                                </div>
                            </div>

                        </div>
                    </div>
                    <div class="mt-3">
                        <p class="cv1">
                            <b class="col-ppd">Audio</b>
                        </p>

                        <table class="table table-striped mb-0">
                            <tbody><tr>
                                <td><b>Year</b></td>
                                <td><b>Title</b></td>
                                <td><b>Role</b></td>
                                <td><b>Listen</b></td>
                            </tr>

                            </tbody><tbody>
                                <tr v-for="audio in audioData.data.list">
                                    <td>{{audio.year}}</td>
                                    <td>{{audio.title}}</td>
                                    <td>{{audio.type}}</td>
                                    <td><a :href="audio.youtube_link" class="btn" target="_blank">Click To Listen</a></td>
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
import axios from 'axios';
import Loader from '../template/loader';

// Social Sharing
import VueGoodshareFacebook from "vue-goodshare/src/providers/Facebook.vue";
import VueGoodshareTwitter from "vue-goodshare/src/providers/Twitter.vue";
import VueGoodshareLinkedIn from "vue-goodshare/src/providers/LinkedIn.vue";
import VueGoodshareWhatsApp from "vue-goodshare/src/providers/WhatsApp.vue";
import html2canvas from 'html2canvas';
import * as jsPDF from 'jspdf'




export default {
	name: 'applicantProfile',
	data() {
		return {
			loading: true,
			profileData: '',
			token: '',
			photoData: '',
			videoData: '',
			audioData: '',
			eduData: '',
			error: '',
            currentUrl: '',
			formLoading: '',
			siteUrl: 'https://api.cast.i.ng/',
            siteUrlshare: 'https://cast.i.ng/#',
		};
	},
	components: {
		loader: Loader,
        VueGoodshareFacebook,
        VueGoodshareTwitter,
        VueGoodshareLinkedIn,
        VueGoodshareWhatsApp
	},
	mounted() {

        this.currentUrl = this.siteUrlshare + this.$route.path;

		this.token = JSON.parse(localStorage.getItem('token'));
		console.log(this.token);

		this.loading = true;

		var config = {
			headers: { 'Access-Control-Allow-Origin': '*' },
		};

		let userID = this.$route.params.id;
		// console.log(userID);

		axios({ method: 'GET', url: 'https://api.cast.i.ng/userdetails/' + userID, config }).then(
			result => {
				this.loading = false;
				this.profileData = result;
			},
			error => {
				this.loading = false;
				console.log('API CALL FAILED');
				console.error(error);
			}
		);

		// Photos API
		axios({ method: 'GET', url: 'https://api.cast.i.ng/myphoto/' + userID, config }).then(
			result => {
				this.loading = false;
				this.photoData = result;
			},
			error => {
				this.loading = false;
				console.log('API CALL FAILED');
				console.error(error);
			}
		);

		// Video API
		axios({ method: 'GET', url: 'https://api.cast.i.ng/myvideo/' + userID, config }).then(
			result => {
				this.loading = false;
				this.videoData = result;
			},
			error => {
				this.loading = false;
				console.log('API CALL FAILED');
				console.error(error);
			}
		);

		// Audio API
		axios({ method: 'GET', url: 'https://api.cast.i.ng/myaudio/' + userID, config }).then(
			result => {
				this.loading = false;
				this.audioData = result;
			},
			error => {
				this.loading = false;
				console.log('API CALL FAILED');
				console.error(error);
			}
		);

		this.token = JSON.parse(localStorage.getItem('token'));
		console.log(this.token);

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
        pdfGenerate(){
            html2canvas(document.querySelector("#capture")).then(canvas => {
                // document.body.appendChild(canvas)

                $("#appendImg").append(canvas);

                var doc = new jsPDF();
                var specialElementHandlers = {
                    '#editor': function (element, renderer) {
                        return true;
                    }
                };


                doc.addImage(canvas, 'JPEG', 10, 10, 180, 200);

                // doc.fromHTML($('#appendImg').html(), 15, 15, {
                //         'width': 170,
                //             'elementHandlers': specialElementHandlers
                //     });
                    doc.save(this.profileData.data.profile.lastname + '.pdf');

            });
            
        },
        downloadImg(){

        }
    },
};
</script>

<style>
.gm-style-mtc {
	display: none !important;
}
.gm-svpc {
	display: none !important;
}
.google-input input {
	background: white;
	padding: 7px 21px;
	border: 1px solid #ccc;
	border-radius: 3px;
	width: 100%;
	box-sizing: border-box;
	color: #3c3c3c;
	font-size: 12px;
}

.msform input[type='url'],
.msform input[type='number'],
.msform input[type='email'],
.msform input[type='date'],
.msform input[type='time'] {
	padding: 6px;
	border: 1px solid #ccc;
	border-radius: 3px;
	width: 100%;
	box-sizing: border-box;
	color: #2c3e50;
	font-size: 13px;
}
.d-inline {
	display: inline-block;
}
.img-preview{
    width: 100%;
    height: 140px;
    border-radius: 8px;
    background-size: cover!important;
    background-position: center!important;
}
.dropdown-menu li a {
    color: white!important;
    width: 97%;
}
.dropdown-menu{
    padding: 6px;
    left: 86px!important;
}
#appendImg{
    display: none;
}
.asPDF{
    float: right;
    border-radius: 3px;
    color: white!important;
    background-color: #de0202;
    padding: 7px 10px;
    font-size: 12px;
    margin-bottom: 18px;
    margin: -5px 1.5px;
}
.asPDF span{
    margin-right: 10px;
}
@media only screen and (max-width: 640px) {
  /* Add your custom styles here for Mobile */
  .img-preview{
    height: 200px!important;
  }
}
</style>