<template>
    <div>
		<styles/>
        <loader v-if="loading"/>
         <section>
            <div class="container">
                <div class="row">
                <div id="page2">
                    <div class="round" align="center">

                    <h3 class="text-center col-p">Forgot Password</h3>
                    <small class="text-center col-pk">RESET YOUR PASSWORD</small>
                    <div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="error">{{ error }}</div>
                    <form class="msform mt-4" @submit.prevent="forgotPassword">

                        <input class="mb-2" v-model="emailAddress" type="text" placeholder="Email" required/>
                        <button type="submit" class="btn btn-ppd btn-block wd">
                        	<img v-if="formLoading" class="form-loader" src="../../assets/images/white-loader.svg" alt="Loader" />
                 	 		<span v-if="!formLoading">Submit</span>
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
	name: 'Forgotpassword',
	components: {
		loader: Loader,
		styles: Styles,
	},
	data() {
		return {
			loading: true,
			emailAddress: '',
			formLoading: false,
			error: false,
		};
	},
	methods: {
		forgotPassword(){

			let form = new FormData();
      		form.append('email',this.emailAddress );

      		this.formLoading = true;

      		const API_URL = process.env.API_URL || 'https://api.cast.i.ng'

      		axios.post(API_URL + '/forgotpassword', form).then(result => {

          this.formLoading = false;
          
          console.log(result.data)
          this.error = result.data.status_msg;
          this.status = result.data.status;
          if(this.status){
            // Clear data
            this.emailAddress = '';
          }


          }, error => {
              this.formLoading = false;
              this.error = 'Failed to send Email';
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