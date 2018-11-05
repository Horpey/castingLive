<template>
    <div>
    	<Styles />
    	<div class="container centrall" style="margin-top: 80px;">
    		<div class="row">
    			<div class="col-md-5">
    				<img src="../../assets/images/castb.png" class="img-responsive img-chair">
    			</div>
    			<div class="col-md-7">
    				<h1 class="fouro">404</h1>
    				<p class="oops">Oops! Why am I here?</p>
    				<p>We are very sorry for the inconvenience. It kooks lkike you're trying to access a page that either has been deleted or never even existed.</p>
    				<router-link class="btn btn-danger btn-pink" v-bind:to="'/Home'">Take me Home</router-link>
    				
    			</div>
    		</div>
    	</div>
    </div>
</template>

<script>
import Styles from './Styles';
    export default {
        name: 'notFound',
        components: {
        	Styles
        }
    }
</script>

<style>


</style>