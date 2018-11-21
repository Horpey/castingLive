<template>
    <div>
		<styles/>
        <loader v-if="loading"/>
         <section>
            <div class="container">
                <div class="row">
                <div id="page2">
                    <div class="round" align="center">

                    <h3 class="text-center col-p">Reset Password</h3>
                    
                    <form class="msform mt-4" @submit.prevent="forgotPassword">

                        <input class="mb-2" v-model="password1" type="password" placeholder="New Password" required/>
                        <input class="mb-2" v-model="password2" type="password" placeholder="Confirm Password" required/>

                        <div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="error">{{ error }}</div>

                        <button type="submit" class="btn btn-ppd btn-block wd">
                        	<img v-if="formLoading" class="form-loader" src="../../assets/images/white-loader.svg" alt="Loader" />
                 	 		<span v-if="!formLoading">Reset Password</span>
                        </button>
                        Don't have an account?
                        <router-link class="col-pk" v-bind:to="'/register'">Create an account</router-link>
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
	name: 'ResetPassword',
	components: {
		loader: Loader,
		styles: Styles,
	},
	data() {
		return {
			loading: true,
			password1: '',
      password2: '',
			formLoading: false,
			error: false,
		};
	},
	methods: {
		forgotPassword(){

			let form = new FormData();
      		form.append('password',this.password1 );
          form.append('password2',this.password2);

          let resetID = this.$route.params.id;


      		this.formLoading = true;

      		const API_URL = process.env.API_URL || 'https://api.cast.i.ng'

      		axios.post(API_URL + '/resetpassword/'+resetID, form).then(result => {

          this.formLoading = false;
          
          console.log(result.data)
          this.error = result.data.status_msg;
          this.status = result.data.status;
          if(this.status){
            // Clear data
            this.password1 = '';
            this.password2 = '';
          }


          }, error => {
              this.formLoading = false;
              this.error = 'Failed to Reset Password';
              console.error(error);
      });
		}
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
      inner: 'Reset Password'
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