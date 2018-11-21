<template>
    <div>
        <!-- Navigation Bar-->

        <header id="topnav" >

            <div class="topbar-main">
                <div class="container">

                    <!-- Logo container-->
                    <div class="logo">
                        <!-- Image Logo -->
                        <router-link class="logo" v-bind:to="'/dashboard/home'">
                            <img src="../../../assets/images/logo-sm.png" alt="" height="50" class="logo-small" />
                            <img src="../../../assets/images/logo.png" alt="" class="logo-large" />
                        </router-link>

                    </div>
                    <!-- End Logo container-->

                    <div class="menu-extras topbar-custom">

                        <ul class="list-inline float-right mb-0 ">

                            <!-- <li class="list-inline-item dropdown notification-list">
                                <div class="list-inline-item hide-phone app-search">
                                    <form role="search" class="">
                                        <div class="form-group pt-1">
                                            <input type="text" class="form-control" placeholder="Search.." />
                                            <a href="#"><i class="fa fa-search"></i></a>
                                        </div>
                                    </form>
                                </div>
                            </li> -->

                            <li class="list-inline-item dropdown notification-list">
                                <a class="nav-link dropdown-toggle arrow-none waves-effect" data-toggle="dropdown" href="#"
                                    role="button" aria-haspopup="false" aria-expanded="false">
                                    <i class="fa fa-bell noti-icon"></i>
                                    <span class="badge badge-danger noti-icon-badge">{{notificationCount.data.count}}</span>
                                </a>
                                <div class="dropdown-menu dropdown-menu-right dropdown-arrow dropdown-menu-lg">
                                    <!-- item-->
                                    <div class="dropdown-item noti-title">
                                        <h5>Notification</h5>
                                    </div>

                                    <!-- item-->

                                    <router-link v-bind:to="'/dashboard/notifications'" class="dropdown-item notify-item"
                                        v-for="notification in notification.data.list" :key="notification">
                                        <div class="notify-icon bg-primary"><i class="fa fa-user"></i></div>
                                        <p class="notify-details"><b>{{notification.title}}</b><small class="text-muted">{{notification.message}}</small></p>
                                    </router-link>



                                    <!-- All-->
                                    <router-link v-bind:to="'/dashboard/notifications'" class="dropdown-item notify-item">View
                                        All
                                    </router-link>
                                    <!-- All-->
                                    <router-link v-bind:to="'/dashboard/settings'" class="dropdown-item notify-item settings"><span class="fa fa-cog"></span>  Notifications Settings
                                    </router-link>

                                </div>
                            </li>
                            <li class="list-inline-item dropdown notification-list">
                                <div class="dropdown notification-list nav-pro-img">
                                    <a class="dropdown-toggle nav-link arrow-none waves-effect nav-user" data-toggle="dropdown"
                                        href="#" role="button" aria-haspopup="false" aria-expanded="false">
                                        <img :src="profileData.data.profile.image" alt="user" class="rounded-circle" />
                                    </a>
                                    <div class="dropdown-menu dropdown-menu-right profile-dropdown ">
                                        <!-- item-->
                                        <div class="dropdown-item noti-title">
                                            <h5>Welcome</h5>
                                        </div>
                                        <router-link v-bind:to="'/dashboard/profile'" class="dropdown-item">
                                            <i class="fa fa-user m-r-5 text-muted"></i>
                                            {{profileData.data.profile.firstname}}
                                        </router-link>


                                        <div class="dropdown-divider"></div>
                                        <a style="cursor: pointer;" class="dropdown-item" v-on:click="logOut"><i class="fa fa-sign-out m-r-5 text-muted"></i>
                                            Logout</a>
                                    </div>
                                </div>
                            </li>
                            <li class="menu-item list-inline-item">
                                <!-- Mobile menu toggle-->
                                <button v-on:click="toggleCla" style="cursor: pointer" class="navbar-toggle nav-link">
                                    <div class="lines">
                                        <span></span>
                                        <span></span>
                                        <span></span>
                                    </div>
                                </button>
                                <!-- End mobile menu toggle-->
                            </li>
                        </ul>

                    </div>
                    <!-- end menu-extras -->

                    <div class="clearfix"></div>

                </div> <!-- end container -->
            </div>
            <!-- end topbar-main -->


            <!-- MENU Start -->
            <div class="navbar-custom">
                <div class="container">
                    <div id="navigation">
                        <!-- Navigation Menu-->
                        <ul class="navigation-menu">
                            <li class="has-submenu ">
                                <router-link v-bind:to="'/dashboard/home'">
                                    <i class="fa fa-tachometer"></i>Dashboard
                                </router-link>
                            </li>

                            <li class="has-submenu">
                                <router-link v-bind:to="'/dashboard/auditions'">
                                    <i class="fa fa-users"></i>Auditions
                                </router-link>
                            </li>


                            <li class="has-submenu ">
                                <router-link v-bind:to="'/dashboard/profile'">
                                    <i class="fa fa-user"></i>My Profile
                                </router-link>

                            </li>

                            <li class="has-submenu">
                                <router-link v-bind:to="'/dashboard/photo'">
                                    <i class="fa fa-picture-o"></i>Photo Gallery
                                </router-link>
                            </li>

                            <li class="has-submenu">
                                <router-link v-bind:to="'/dashboard/video'">
                                    <i class="fa fa-video-camera"></i>Video
                                </router-link>
                            </li>

                            <li class="has-submenu">
                                <router-link v-bind:to="'/dashboard/audio'">
                                    <i class="fa fa-volume-up"></i>Audio
                                </router-link>
                            </li>
                        </ul><!-- End navigation menu -->

                    </div> <!-- end #navigation -->
                </div> <!-- end container -->
            </div> <!-- end navbar-custom -->

            

        </header>

        
            <div class="sidebar-toggle hidden-desktop">
                <div class="">
                    <div class="sidebar-bg" :style="{'background': ' url('+ profileData.data.profile.image + ')' }"></div>
                    <div class="">
                        <p style="font-size: 18px; font-weight: bold;" class="text-white text-center">{{profileData.data.profile.firstname}} {{profileData.data.profile.lastname}}</p>
                        <div class="text-center">
                            <router-link class="btn-side btn" v-bind:to="'/dashboard/editProfile'">Edit</router-link>
                            <!-- <router-link class="btn-side btn" v-bind:to="'/director/profile'">View</router-link> -->
                    </div>
                    </div>
                </div>
                <div class="">
                    <ul class="side-ul">
                        <li v-on:click="toggleCla" class="sidebar-list">
                            <router-link v-bind:to="'/dashboard/home'">Dashboard
                            </router-link>
                        </li>

                        <li v-on:click="toggleCla" class="sidebar-list">
                            <router-link v-bind:to="'/dashboard/auditions'">Auditions
                            </router-link>
                        </li>

                        <li v-on:click="toggleCla" class="sidebar-list">
                            <router-link v-bind:to="'/dashboard/profile'">My Profile
                            </router-link>
                        </li>

                        <li v-on:click="toggleCla" class="sidebar-list">
                            <router-link v-bind:to="'/dashboard/photo'">Photo Gallery
                            </router-link>
                        </li>

                        <li v-on:click="toggleCla" class="sidebar-list">
                            <router-link v-bind:to="'/dashboard/video'">Video
                            </router-link>
                        </li>

                        <li v-on:click="toggleCla" class="sidebar-list">
                            <router-link v-bind:to="'/dashboard/audio'">Audio
                            </router-link>
                        </li>

                        <li class="sidebar-list">
                            <a style="color: white; cursor: pointer" v-on:click="logOut">Logout
                            </a>
                        </li>

                        <li>
                            <p class="quick">Access Cast.i.ng quicker: Go to your browser's menu and click "Add to Home screen"</p>
                        </li>
                    </ul>
                </div>
            </div>
       
        <!-- End Navigation Bar-->
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name: 'navHeader',
        data() {
            return {
                sideTogg: true,
                loading: true,
                profileData: '',
                token: '',
                toggled: false,
                notificationCount: '',
                notification: '',
                siteUrl: 'https://api.cast.i.ng/',
            };
        },
        methods: {
            logOut() {
                localStorage.removeItem('token');
                this.$router.push('/home');
                // this.$router.replace(this.$route.query.redirect || '/about')
            },
            toggleCla(){
                // this.toggleActive = !this.toggleActive;
                $('.sidebar-toggle').toggleClass( "sidebarToggleActive" );
            }
        },
        mounted() {
            // console.log(this.toggled);
            this.token = JSON.parse(localStorage.getItem('token'));
            console.log(this.token);

            this.loading = true;

            var config = {
                headers: {
                    'Access-Control-Allow-Origin': '*'
                },
            };

            let userID = JSON.parse(localStorage.getItem('token'));
            // console.log(userID);

            axios({
                method: 'GET',
                url: 'https://api.cast.i.ng/userdetails/' + userID,
                config
            }).then(
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

            axios({
                method: 'GET',
                url: 'https://api.cast.i.ng/user/notification/count/' + userID,
                config
            }).then(
                result => {
                    this.loading = false;
                    this.notificationCount = result;
                },
                error => {
                    this.loading = false;
                    console.log('API CALL FAILED');
                    console.error(error);
                }
            );

            axios({
                method: 'GET',
                url: 'https://api.cast.i.ng/user/notification/list/' + userID + '?limit=4',
                config
            }).then(
                result => {
                    this.loading = false;
                    this.notification = result;
                },
                error => {
                    this.loading = false;
                    console.log('API CALL FAILED');
                    console.error(error);
                }
            );
        },
    };
</script>

<style>
.settings, .settings:hover{
    background-color: #3f0048;
    color: white;
    font-weight: bold;
}
#sidebar-wrapper{
    left: 0!important;
}
.toggleside{
    margin-left: 0px;
}
.sidebar-nav{
    position: fixed;
    top: 0;
    width: 250px;
    margin: 0;
    z-index: 99999;
    height: 100vh;
    padding: 0;
    list-style: none;
    background-color: #3f0048;
}
.sidebar-toggle{
    background: linear-gradient(#e6077c,#690037);
    height: 100vh;
    overflow-y: scroll;
    width: 80%;
    box-shadow: 5px 0px 8px 0px #0000003d;
    left: -83%;
    position: fixed;
    -webkit-transition: 0.5s all;
    transition: 0.5s all;
    z-index: 9999;
}
.sidebarToggleActive{
    left: 0!important;
}
.sidebar-bg{
    border-radius: 400px;
    width: 150px;
    margin: 0 auto;
    height: 150px;
    background-size: cover!important;
    background-position: center!important;
    margin: 32px auto 12px;
    border: 7px solid #ffffff70;
}
.btn-side{
    background-color: white;
    padding: 2px 20px;
    border: white;
}
.side-ul{
    padding-left: 18px;
    list-style: none;
    margin: 23px 0px;
}
.side-ul li a{
    font-size: 16px;
    padding: 13px 34px;
    display: block;
    border-top-left-radius: 45px;
    border-bottom-left-radius: 45px;
    color: white;  
}
.side-ul li a.router-link-active{
    font-size: 16px;
    background-color: #ffffff;
    padding: 13px 34px;
    display: block;
    border-top-left-radius: 45px;
    border-bottom-left-radius: 45px;
    color: black;
}
.quick{
        color: white;
    font-size: 14px;
    margin: 20px 30px;
    border-top: 1px solid #0000006b;
    padding: 9px 0px;
}
.sidebar-toggle-active{

}

@media (min-width:992px){
    .hidden-desktop{
        display:none!important
    }
}

</style>