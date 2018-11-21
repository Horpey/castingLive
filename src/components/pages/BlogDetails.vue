<template>
    <div>
      <loader v-if="loading"/>
        <header class="sub-ban1 clippath" :style="{'background': 'linear-gradient(180deg, #000c, #00000080), url('+ require ('../../assets/images/background.jpg') + ')'}">
      <div class="container">
        <div class="row">
          <div class="col-lg-12 mx-auto text-white pt-c2">
            <h4>Blog</h4>
            <router-link class="text-white" v-bind:to="'/Home'">Home</router-link>

            <i class="fa fa-angle-double-right mr-2 ml-2"></i>
            <router-link class="text-white" v-bind:to="'/Blog'">Blog</router-link>
            <i class="fa fa-angle-double-right mr-2 ml-2"></i>
            <small>{{blogDetailss.blog_title}}</small>
          </div>
        </div>
      </div>
    </header>


    <section class="sec-3">
      <div class="container">
        <div class="row">
          <div class="col-lg-8">

            <h3 class="col-p slider-head">{{blogDetailss.blog_title}}</h3>
            <label>
              <i class="fa fa-calendar"></i> {{blogDetailss.blog_created}} 
            </label>
            <img :src="blogDetailss.blog_image" class="rounded img-fluid" />
            <div style="margin-top: 20px!important;" class="mt-2" v-html="blogDetailss.blog_content"></div>


          </div>


          <div class="col-lg-4">
            <h3 class="col-p">Popular Post</h3>

            <div class="row">
              <div class="col-lg-12 mb-2" v-for="popularBlog in popularList">
                <div class="row">
                  <div class="col-md-4">
                    <img :src="popularBlog.image" width="120" height="70" class="rounded float-left mr-2" />
                  </div>
                  <div class="col-md-8">
                    <p style="font-weight: bold; margin: 0px; font-size: 13px;">
                      <router-link class="col-pk" v-bind:to="'/blogdetails/'+popularBlog.id" >{{popularBlog.title}}</router-link>
                    </p>
                    <p style="font-size: 13px; margin: 0px;">
                    <i class="fa fa-calendar col-b"></i>
                    <span>{{popularBlog.created | moment().format("DD MMM YYYY")}}</span>
                    </p>
                  </div>
                </div>
                <div class="bline" style="padding-top: 0px;"></div>
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
	name: 'blogdetails',
	data() {
		return {
			loading: true,
      hhh: 'Hello H',
      blogDetailss: '',
      popularList: '',
      blogTitle: '',
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
        headers: {
            'Access-Control-Allow-Origin': '*'
        },
    };

    let blogID = this.$route.params.id;

  axios({
      method: 'GET',
      url: 'https://api.cast.i.ng/getblog/'+blogID,
      config
  }).then(
      result => {
          this.loading = false;
          this.blogDetailss = result.data;
          this.popularList = result.data.popular_list;
          console.log(this.blogDetailss.blog_title);
          this.blogTitle = this.blogDetailss.blog_title;
          return this.blogTitle;
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
      inner: 'Blog'
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
</style>