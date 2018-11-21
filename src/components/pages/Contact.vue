<template>
    <div>
      <loader v-if="loading"/>
         <header class="sub-ban1 clippath" :style="{'background': 'linear-gradient(180deg, #000c, #00000080), url('+ require ('../../assets/images/background.jpg') + ')'}">
      <div class="container">
        <div class="row">
          <div class="col-lg-12 mx-auto text-white pt-c2">
            <h4>Contact Us</h4>
            <small>HOME</small>
            <i class="fa fa-angle-double-right mr-2 ml-2"></i>
            <small>Contact</small>
          </div>
        </div>
      </div>
    </header>


    <section class="sec-5" style="padding-bottom: 120px;">
      <div class="container">
        <div class="row">
          <div class="col-lg-8">
            <div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="error">{{ error }}</div>

            <form class="msform mt-4" @submit.prevent="sendContact">
              <div class="row">
                <div class="col-lg-6">
                  <b>Full Name</b>
                  <input v-model="fullName" class="mb-2" type="text" placeholder="Full Name" required="" />
                  <b>Company</b>
                  <input v-model="company" class="mb-2" type="text" placeholder="Company Name" />
                </div>
                <div class="col-lg-6">
                  <b>Email Address</b>
                  <input v-model="emailAddress" class="mb-2" type="email" placeholder="Email Address" required="" />
                  <b>Contact Number</b>
                  <input v-model="contactNumber" class="mb-2" type="text" placeholder="Phone Number" />
                </div>
                <div class="col-lg-12">
                  <b>Your Message</b>
                  <textarea v-model="message" class="mb-2" row="" required=""></textarea>
                  <button type="submit" class="btn btn-ppd btn-block wd">
                    <img v-if="formLoading" class="form-loader" src="../../assets/images/white-loader.svg" alt="Loader" />
                    <span v-if="!formLoading">Send Message</span>
                  </button>
                </div>
              </div>
            </form>
          </div>


          <div class="col-lg-4">
            <!-- <h2 class="col-p slider-head mt-5">Cast.i.ing Contact Details</h2> -->
            <p class="feelFree">Feel free to contact us for questions</p>
            <b>Address:</b> {{contactDetails.address}}
            <br>
            <b>Email:</b> {{contactDetails.email}}
            <br>
            <b>Phone:</b> {{contactDetails.phone}}
            <br>
            <br>

            <a target="_blank" :href="contactDetails.facebook_link">
              <i class="fa fa-2x fa-facebook-square" style="color:#3b5998;"></i>
            </a>
            <a target="_blank" :href="contactDetails.twitter_link">
              <i class="fa fa-2x fa-twitter-square" style="color:#08a0e9;"></i>
            </a>
            <a target="_blank" :href="contactDetails.linkedin_link">
              <i class="fa fa-2x fa-linkedin-square" style="color:#0077b5;"></i>
            </a>
            <a target="_blank" :href="contactDetails.instagram_link">
              <i class="fa fa-2x fa-instagram" style="color:#da1a42;"></i>
            </a>

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
	name: 'Contact',
	data() {
		return {
			loading: true,
      formLoading: false,
      error: false,
      fullName: '',
      company: '',
      emailAddress: '',
      contactNumber: '',
      message: '',
      formLoading: false,
      contactDetails: ''
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

    axios.get('http://api.cast.i.ng/contactdetails').then(
        response => {
            this.contactDetails = response.data;
        },
        error => {
            this.loading = false;
            console.log('Page Error');
        }
    );
	},
  methods: {
    sendContact(){
      let form = new FormData();
      form.append('name',this.fullName );
      form.append('company',this.company );
      form.append('email',this.emailAddress );
      form.append('phone',this.contactNumber );
      form.append('message',this.message );




      this.formLoading = true;

      const API_URL = process.env.API_URL || 'https://api.cast.i.ng'

      axios.post(API_URL + '/contactus', form).then(result => {

          this.formLoading = false;
          
          // console.log(result.data)
          this.error = result.data.status_msg;
          this.status = result.data.status;
          if(this.status){
            // Clear data
            this.fullName = '';
            this.company = '';
            this.emailAddress = '';
            this.contactNumber = '';
            this.message = '';
          }


          }, error => {
            this.formLoading = false;
              console.error(error);
      });
    }
  },
  head: {
    title: {
      inner: 'Contact'
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
.form-loader{
    width: 22px;
}
.success{
  color: #155724;
  background-color: #d4edda;
  border-color: #c3e6cb;
}
.danger{
    color: #721c24;
    background-color: #f8d7da;
    border-color: #f5c6cb;
}

.feelFree{
      font-size: 25px;
    color: #e7077d;
    line-height: 1;
}
</style>