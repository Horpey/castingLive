<template>
    <div>
        <loader v-if="loading"/>
        <header class="sub-ban-nn" :style="{'background': 'linear-gradient(180deg, #000c, #00000080), url('+ require ('../../assets/images/background.jpg') + ')'}">
            <div class="container about-headd" style="padding-top: 175px;">
                <div class="row">
                    <div class="col-lg-7 mx-auto text-white text-center">
                        <h2>The best talents in the land get hired here</h2>
                        <p>We provide the the most convenient place for talented actors and the casting Directors who need their
                            services to meet, and get work started.</p>
                    </div>
                </div>
            </div>
        </header>


<section id="prices r-prices" style="margin-bottom: 80px; margin-top: 70px;">
    <div class="container">
        <div class="row">
            <div class="col-md-4">
                <div class="pricing-card pricing-card-free">
                    <h3 class="price-type">FREEMIUM</h3>
                    <!-- <h3 class="price-amount">N0.00</h3> -->
                    <p class="price-exer">Per Month, billed annually or N0.00 billed Monthly</p>
                    <hr>
                    <p><b>Features</b></p>
                    <ul class="price-feat">
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Create a Full Profile Resume</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Add 3 Headshots</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">View Audition Notices</div>
                            </div>
                        </li>
                    </ul>
                    <router-link class="btn btn-price btn-block text-white" v-bind:to="'/register'">Get Started</router-link>
                </div>
            </div>

            <div class="col-md-4">
                <div class="pricing-card pricing-card-premium">
                    <h3 class="price-type">PREMIUM</h3>
                    <!-- <h3 class="price-amount">N10.00</h3> -->
                    <p class="price-exer">Per Month, billed annually or N0.00 billed Monthly</p>
                    <hr>
                    <p><b>Features</b></p>
                    <ul class="price-feat">
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Create a Full Profile Resume</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Add 3 Headshots</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">View Audition Notices</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Create a Full Profile Resume</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Add 3 Headshots</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">View Audition Notices</div>
                            </div>
                        </li>
                    </ul>

                    <router-link class="btn btn-price btn-block text-white" v-bind:to="'/register'">Get Started</router-link>

                </div>
            </div>

            <div class="col-md-4">
                <div class="pricing-card pricing-card-titanium">
                    <h3 class="price-type">TITANIUM</h3>
                    <!-- <h3 class="price-amount">N20.00</h3> -->
                    <p class="price-exer">Per Month, billed annually or N0.00 billed Monthly</p>
                    <hr>
                    <p><b>Features</b></p>
                    <ul class="price-feat">
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Create a Full Profile Resume</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Add 3 Headshots</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">View Audition Notices</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Create a Full Profile Resume</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Add 3 Headshots</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">View Audition Notices</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Create a Full Profile Resume</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">Add 3 Headshots</div>
                            </div>
                        </li>
                        <li class="mb-1">
                            <div class="row">
                                <div class="col-1"><span class="feat-avail fa fa-check"></span></div>
                                <div class="col-10" style="padding-left: 27px;">View Audition Notices</div>
                            </div>
                        </li>
                    </ul>

                    <router-link class="btn btn-price btn-block text-white" v-bind:to="'/Contact'">Contact Us</router-link>
                </div>
            </div>

        </div>
    </div>
</section>


<section id="prices r-prices" style="margin-bottom: 80px;">
   <!--  <div class="container">
        <div class="my-4" align="center">
            <small class="r-small">SELECT A SUBCRIPTION PLAN</small>
            <h1 class="col-p slider-head">Subscription to a Package</h1>
        </div>
        <div class="row">
            <div class="col-xs-12 col-md-12">
                <div class="table-responsive">
                    <table class="pricing-table table-responsive">
                        <tbody>
                            <tr>
                                <td width="30%" class="pricing-table-text">
                                    <h2 class="mr-1 table-nnn">Select the package that best suits your needs.</h2>
                                    <p id="col-pk">Pay monthly, or save big with an annual subscription.</p>
                                </td>
                                <td width="20%">
                                    <div class="pricing-table-item">
                                        <div class="pricing-table-item-head" id="bdg">
                                            <p>FREEMIUM</p>
                                        </div>
                                        <div class="pricing-table-item-purchase" style="padding: 0px; border-radius:  0px;">
                                            <router-link class="btn btn-ppd btn-block" style="border-radius:  0px; border-top: 2px solid #630071;" v-bind:to="'/register'">Register Now</router-link>
                                        </div>
                                    </div>
                                </td>
                                <td width="20%">
                                    <div class="pricing-table-item">
                                        <div class="pricing-table-item-head" id="bdg1">
                                            <p>PREMIUM</p>
                                        </div>
                                        <div class="pricing-table-item-purchase" style="padding:  0px;">

                                            <router-link class="myBtn btn btn-bb btn-primary" style="border-radius:  0px;width:  100%;border-top: 2px solid #52d4e6;" v-bind:to="'/register'">Get Started</router-link>
                                        </div>
                                    </div>
                                </td>
                                <td width="20%">
                                    <div class="pricing-table-item">
                                        <router-link v-bind:to="'/contact'" class="text-white">
                                            <div class="pricing-table-item-head" id="bdg2" style="padding: 29px 0px;margin-top: 0px;">
                                                    <p>TITANIUM</p>
                                            </div>
                                        </router-link>
                                        
                                    </div>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Create a Full Profile Resume</td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Add Headshots</td>
                                <td>1</td>
                                <td>10</td>
                                <td>10</td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Add Video Reel</td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Add Voice Reel</td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>View Audition Notices</td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Apply and Book Unlimited Auditions</td>
                                <td>1</td>
                                <td>Unlimited</td>
                                <td>Unlimited</td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Health Insurance</td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Monthly Spa Treatment</td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Gym Registration</td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Stylist and Wardrobe Consultation</td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                            <tr class="pricing-table-list">
                                <td>Voice training</td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-times text-danger"></i>
                                </td>
                                <td>
                                    <i class="fa fa-check text-success"></i>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

        </div>
    </div> -->
</section>

    </div>
</template>

<script>
import axios from 'axios';
import Loader from '../template/loader';

export default {
	name: 'pricing',
	data() {
		return {
			loading: true,
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
	},
    head: {
      title: {
        inner: 'Subscription'
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
.pricing-table {
	margin-bottom: 100px;
}
.sub-ban-nn{
        min-height: 400px;
    background-size: cover!important;
    -webkit-clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
    clip-path: polygon(100% 0, 100% 69%, 28% 100%, 0 79%, 0 0);
}

.pricing-card{
    padding: 30px 25px;
    border-radius: 5px;
    box-shadow: 0px 0px 9px 0px #0000003d;
}
.pricing-card-free{
    border-top: 7px solid #e7077d;
}

.pricing-card-free .price-type{
    background-color: #e7077d;
}

.pricing-card-free .btn-price{
    background-color: #e7077d;
}

.pricing-card-premium {
    border-top: 7px solid #23b3c7;
}

.pricing-card-premium  .price-type{
    background-color: #23b3c7;
}

.pricing-card-premium  .btn-price{
    background-color: #23b3c7;
}

.pricing-card-titanium{
    border-top: 7px solid #3f0048;
}

.pricing-card-titanium .price-type{
    background-color: #3f0048;
}

.pricing-card-titanium .btn-price{
    background-color: #3f0048;
}





.btn-price{
        font-size: 16px;
    font-weight: normal;
}

.price-type{
    font-size: 20px;
    display: inline-block;
    font-weight: bold;
    color: white;
    padding: 10px 17px;
    border-radius: 4px;
}
.price-amount{
    font-size: 50px;
}
.price-exer{
        font-size: 14px;
    color: darkgray;
}

.price-feat{
        list-style: none;
    padding-left: 0px;
}

.feat-avail{
        background-color: #13b905;
    padding: 8px;
    color: white;
    border-radius: 33px;
    font-size: 12px;
}
</style>