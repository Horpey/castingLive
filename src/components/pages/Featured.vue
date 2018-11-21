<template>
    <div>
      <loader v-if="loading"/>
         <header class="sub-ban1 clippath" :style="{'background': 'linear-gradient(180deg, #000c, #00000080), url('+ require ('../../assets/images/background.jpg') + ')'}">
      <div class="container">
        <div class="row">
          <div class="col-lg-12 mx-auto text-white pt-c2">
            <h4>Featured Actor </h4>
            <small>HOME</small>
            <i class="fa fa-angle-double-right mr-2 ml-2"></i>
            <small>Featured</small>
          </div>
        </div>
      </div>
    </header>


    <section class="sec-5">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="row">
              <div class="col-md-3">
                <div class="feat-img" :style="{'background': 'linear-gradient(rgba(255, 255, 255, 0), rgba(0, 0, 0, 0.5)), url('+ profileData.profile.image + ')'}">
                </div>
              </div>
              <div class="col-md-8">
                <h3>{{profileData.profile.firstname}} {{profileData.profile.lastname}}</h3>
                <p><i>{{profileData.profile.description}}</i></p>
                <hr>
                <div class="row">
                  <div class="col-md-6">
                    <h4 class="attrr"><b>Attributes</b></h4>
                    <div class="attrr">
                      <p class="my-1">Gender<span class="pull-right">{{profileData.attributes.gender}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">State<span class="pull-right">{{profileData.profile.state}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Height<span class="pull-right">{{profileData.attributes.height}}In</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Weight<span class="pull-right">{{profileData.attributes.weight}}Kg</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Complexion<span class="pull-right">{{profileData.attributes.complexion_title}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Body Mass(in KG)<span class="pull-right">{{profileData.attributes.body_mass}}</span></p>
                      <hr class="no-margin">
                    </div>
                  </div>
                  <div class="col-md-6">
                    <h4 class="attrr"><b>Sizes</b></h4>
                    <div class="attrr">
                      <p class="my-1">Shirt Size (in Inches)<span class="pull-right">{{profileData.attributes.shirt_size}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Waist Size (in Inches)<span class="pull-right">{{profileData.attributes.waist_size}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Trouser length (in Inches)<span class="pull-right">{{profileData.attributes.trouser_length}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Shoulder length (in Inches)<span class="pull-right">{{profileData.attributes.shoulder_length}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Jacket size<span class="pull-right">{{profileData.attributes.jacket_size}}</span></p>
                      <hr class="no-margin">
                      <p class="my-1">Shoe Size<span class="pull-right">{{profileData.attributes.shoe_size}}</span></p>
                      <hr class="no-margin">
                    </div>
                  </div>
                  <div class="col-md-12">
                    <h4 class="attrr" style="margin-top: 14px;"><b>Feature Film</b></h4>
                    <table class="table table-striped mb-0 table-responsive">
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
                            <tr v-for="feature in profileData.featurefilm">
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
                </div>
                <div class="col-md-12">
                  <h4 class="attrr" style="margin-top: 14px;"><b>TV Series</b></h4>
                  <table class="table table-striped mb-0 table-responsive">
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
                          <tr v-for="tv in profileData.tvseries">
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

                <div class="col-md-12">
                  <h4 class="attrr" style="margin-top: 14px;"><b>Web Series</b></h4>
                  <table class="table table-striped mb-0 table-responsive">
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
                          <tr v-for="web in profileData.webseries">
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

                <div class="col-md-12">
                  <h4 class="attrr" style="margin-top: 14px;"><b>Theater/Stage Plays</b></h4>
                  <table class="table table-striped mb-0 table-responsive">
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
                        <tr v-for="theater in profileData.theater">
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

                <div class="col-md-6">
                  <h4 class="attrr" style="margin-top: 14px;"><b>Social Handles</b></h4>
                  <div class="">
                    <a target="_blank" :href="profileData.social.facebook">
                        <i class="fa fa-2x fa-facebook-square" style="color:#3b5998;"></i>
                    </a>
                    <a target="_blank" :href="profileData.social.twitter">
                        <i class="fa fa-2x fa-twitter-square" style="color:#08a0e9;"></i>
                    </a>
                    <a target="_blank" :href="profileData.social.linkedln">
                        <i class="fa fa-2x fa-linkedin-square" style="color:#0077b5;"></i>
                    </a>
                    <a target="_blank" :href="profileData.social.instagram">
                        <i class="fa fa-2x fa-instagram" style="color:#da1a42;"></i>
                    </a>
                  </div>
                </div>

                <div class="col-md-12">
                  <h4 class="attrr" style="margin-top: 14px;"><b>Trainings And Education</b></h4>
                  <table class="table table-striped mb-0">
                      <tbody>
                          <tr v-for="education in profileData.education">
                              <td>
                                  <i class="fa fa-calendar"></i> {{education.year}}</td>
                              <td>{{education.school}}</td>
                              <td>{{education.certificate}}</td>
                          </tr>
                      </tbody>
                  </table>
                </div>

                <div class="col-md-12">
                  <h4 class="attrr" style="margin-top: 14px;"><b>Photo</b></h4>
                  <div class="row no-gutters mt-2">
                      <div class="col-md-3 p-1" v-for="photo in photoData.data.headshot_list">
                          <a :href="siteUrl + photo.image" data-fancybox="gallery">
                              <img class="rounded mx-auto d-block img-fluid" alt="200x200" :src="siteUrl + photo.image" data-holder-rendered="true" />
                          </a>
                      </div>
                  </div>
                </div>

                <div class="col-md-12">
                  <h4 class="attrr" style="margin-top: 14px;"><b>Video</b></h4>
                  
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

                <div class="col-md-12">
                  <h4 class="attrr" style="margin-top: 14px;"><b>Audio</b></h4>
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
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios';
import Loader from '../template/loader';
export default {
	name: 'Featured',
	data() {
		return {
			loading: true,
      profileData: '',
      photoData: '',
      videoData: '',
      audioData: '',
      eduData: '',
      siteUrl: 'https://api.cast.i.ng/',
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

    var config = {
      headers: { 'Access-Control-Allow-Origin': '*' },
    };

    let userID = this.$route.params.id;
    // console.log(userID);

    axios({ method: 'GET', url: 'https://api.cast.i.ng/userdetails/' + userID, config }).then(
      result => {
        this.loading = false;
        this.profileData = result.data;
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

	},
  head: {
    title: {
      inner: 'Featured'
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
.feat-img{
    background-size: cover!important;
    background-position: center!important;
    height: 220px;
    border-radius: 9px;
    width: 100%;
}
.attrr{
      background: #fcfcfc;
    color: #a0a0a0;
    font-size: 18px;
    padding: 9px 17px;
    border-radius: 4px;
    border: 1px solid #dcdcdc;
}
.no-margin{
  margin: 0px;
}
.pull-right{
  float: right;
}
</style>