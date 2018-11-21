<template>
    <div>
        <navHeader/>
		<div class="wrapper">
            <div class="container">
                <div class="row">
					<div class="col-md-12 col-lg-12 col-xl-4">
						<sidebar/>
					</div>
					<div class="col-xl-8">
						<router-view></router-view>
					</div>
                </div>
            </div>
		</div>
        <!-- <siteFooter/> -->
    </div>
</template>

<script>
import navHeader from './template/navHeader';
import sidebar from './template/sidebar';
// import siteFooter from './template/siteFooter';
import Loader from './template/loader';

export default {
	name: 'Index',
	components: {
		navHeader: navHeader,
		sidebar: sidebar,
		// siteFooter: siteFooter,
		loader: Loader,
	},
	data() {
		return {
			loading: true,
		};
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
	updated () {
	    console.log('Meant to go back');
	    if (!localStorage.token && this.$route.path !== '/') {
	      this.$router.push('/?redirect=' + this.$route.path)
	    }
	},
	head: {
      title: {
        inner: 'Dashboard'
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
/* Dashboard Styles */
/*@import '../../assets/assets/css/bootstrap-material-design.min.css';*/
/*@import '../../assets/vendor/bootstrap/css/bootstrap.min.css';*/
/*@import '../../assets/assets/css/icons.css';*/
@import '../../assets/assets/css/style.css';
/*@import '../../assets/assets/css/sidebar.css';*/

.wrapper {
    padding-top: 160px!important;
}

/*
.home-footer {
	display: none !important;
}*/

/*.home-headerr{
	display: none !important;
}*/

.slide-bg {
	height: 200px;
	width: 100%;
	background-size: cover !important;
	background-position: center !important;
}
.text-limit {
	overflow: hidden;
	text-overflow: ellipsis;
	display: -webkit-box;
	line-height: 16px;
	max-height: 97px;
	-webkit-line-clamp: 6;
	-webkit-box-orient: vertical;
}
.text-color {
	color: #e6077c;
}
.text-bold {
	font-weight: bold;
}
.router-link-active i {
	background-color: #22b3c6 !important;
}

.router-link-active {
	border-bottom: 0px !important;
}
.bmd-form-group input[type=date]{
	padding: 6px;
    border: 1px solid #ccc;
    border-radius: 3px;
    width: 100%;
    box-sizing: border-box;
    color: #2C3E50;
    font-size: 13px;
}

.modal-dialog{
  background-color: white!important;
}
</style>