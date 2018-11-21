<template>
    <div>
      <styles/>
      <loader v-if="loading"/>
         <section>
      <div class="container">
        <div class="row">
          <div id="page1">
            <div class="round" align="center">

              <h3 class="text-center col-p">Actors</h3>
              <small class="text-center col-pk">REGISTER TODAY AS AN ACTORS IN CAST.I.NG MANAGER</small>
              
              <form class="msform mt-4" @submit.prevent="registerActor">
                <input class="mb-2" type="text" v-model="firstname" placeholder="First Name" required="">
                <input class="mb-2" type="text" v-model="lastname" placeholder="Last Name" required="">
                <input class="mb-2" type="text" v-model="username" placeholder="Username" required="">
                <input class="mb-2" type="text" v-model="phone" placeholder="Phone Number" required="">
                <input class="mb-2" type="email" v-model="email" placeholder="Email" required="">  
                <select class="mb-2" v-model="gender" required="">
                  <option value="">Select Gender</option>
                  <option value="0">Female</option>
                  <option value="1">Male</option>
                </select>
                 <span class="bmd-form-group is-filled"><select v-model="state_id" class="mb-2" style="margin-top: 8px;">
                  <option value="" selected>Select State Of Residence</option>
                  <option value="1">Abia State</option>
                  <option value="2">Adamawa State</option>
                  <option value="3">Akwa Ibom State</option>
                  <option value="4">Anambra State</option>
                  <option value="5">Bauchi State</option>
                  <option value="6">Bayelsa State</option>
                  <option value="7">Benue State</option>
                  <option value="8">Borno State</option>
                  <option value="9">Cross River State</option>
                  <option value="10">Delta State</option>
                  <option value="11">Ebonyi State</option>
                  <option value="12">Edo State</option>
                  <option value="13">Ekiti State</option>
                  <option value="14">Enugu State</option>
                  <option value="15">FCT</option>
                  <option value="16">Gombe State</option>
                  <option value="17">Imo State</option>
                  <option value="18">Jigawa State</option>
                  <option value="19">Kaduna State</option>
                  <option value="20">Kano State</option>
                  <option value="21">Katsina State</option>
                  <option value="22">Kebbi State</option>
                  <option value="23">Kogi State</option>
                  <option value="24">Kwara State</option>
                  <option value="25">Lagos State</option>
                  <option value="26">Nasarawa State</option>
                  <option value="27">Niger State</option>
                  <option value="28">Ogun State</option>
                  <option value="29">Ondo State</option>
                  <option value="30">Osun State</option>
                  <option value="31">Oyo State</option>
                  <option value="32">Plateau State</option>
                  <option value="33">Rivers State</option>
                  <option value="34">Sokoto State</option>
                  <option value="35">Taraba State</option>
                  <option value="36">Yobe State</option>
                  <option value="37">Zamfara State</option>
              </select></span>
               <input class="mb-2" type="password" v-model="password" placeholder="Password" required="">
               <input class="mb-2" type="password" v-model="password2" placeholder="Confirm Password" required="">
               <input class="mb-2" type="file" @change="processFile($event)" placeholder="Upload Picture" accept="image/*">

               <div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="error">{{ error }}</div>

                <button type="submit" class="btn btn-ppd btn-block wd">
                  <img v-if="formLoading" class="form-loader" src="../../assets/images/white-loader.svg" alt="Loader" />
                  <span v-if="!formLoading">Create an Account</span>
                </button>
              </form>
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
import Styles from '../template/styles';
export default {
	name: 'Registeractor',
	data() {
		return {
			loading: true,
      firstname: '',
      lastname: '',
      username: '',
      phone: '',
      gender: '',
      password: '',
      password2: '',
      image: '',
      email: '',
      status: '',
      state_id: '',
      formLoading: false,
      error: false,
      notExist: ""
		};
	},
	components: {
		loader: Loader,
		styles: Styles,
	},
  methods: {
    processFile(event) {
      event.target.files[0]
      this.image = event.target.files[0];
    },

    registerActor () {

      let form = new FormData();
      form.append('firstname',this.image );
      form.append('firstname',this.firstname );
      form.append('lastname',this.lastname );
      form.append('username',this.username );
      form.append('phone',this.phone );
      form.append('gender',this.gender );
      form.append('state_id',this.state_id );
      form.append('password',this.password );
      form.append('password2',this.password2 );
      form.append('email',this.email );
      

      this.formLoading = true;

      console.log(form);

      const API_URL = process.env.API_URL || 'https://api.cast.i.ng'

      axios.post(API_URL + '/signup/actor', form).then(result => {

          this.formLoading = false;

          if(!result.data.status_msg){
            this.registerSuccessful(result.data)
          }
          
          console.log(result.data)
          this.error = result.data.status_msg;
          this.status = result.data.status;
          if(this.status){
            // Clear data
            this.firstname = '';
            this.lastname = '';
            this.username = '';
            this.phone = '';
            this.gender = '';
            this.password = '';
            this.password2 = '';
            this.email = '';
            this.image = '';
          }


          }, error => {
              () => this.registerFailed()
              console.error(error);
      });
    },

    registerSuccessful (req) {

      // Clear data
      this.firstname = '';
      this.lastname = '';
      this.username = '';
      this.gender = '';
      this.password = '';
      this.password2 = '';
      this.email = '';
      this.image = '',

        console.log(req.page_type);
        
        if (!req.user_id) {
            this.registerFailed()
            return
        }

        if (req.page_type == "actor") {
            localStorage.token = req.user_id
            this.error = false  
            this.$router.replace(this.$route.query.redirect || '/dashboard/home')
        } 
        else if(req.page_type == "casting-director"){
            localStorage.token = req.user_id
            this.error = false  
            this.$router.replace(this.$route.query.redirect || '/director/home')
        }
    },

    registerFailed () {
      this.formLoading = false;
      // Clear data
      this.firstname = '';
      this.lastname = '';
      this.username = '';
      this.gender = '';
      this.password = '';
      this.password2 = '';
      this.email = '';
      this.image = '',

        this.error = 'Registration failed!'
        delete localStorage.token
    },
    checkCurrentLogin (req) {

        if (localStorage.token) {
            if(req.page_type == "actor"){
                this.$router.replace(this.$route.query.redirect || '/dashboard/home')
            } else if(req.page_type == "casting-director"){
                this.$router.replace(this.$route.query.redirect || '/director/home')
            }
        }
    }



  },
  updated () {
      this.checkCurrentLogin()
  },
  created () {
      this.checkCurrentLogin()
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
  head: {
    title: {
      inner: 'Actor'
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
</style>