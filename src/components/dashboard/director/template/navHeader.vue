<template>
    <div>
        <!-- Navigation Bar-->
        <header id="topnav">
            <div class="topbar-main">
                <div class="container">

                    <!-- Logo container-->
                    <div class="logo">
                        <!-- Image Logo -->
                        <router-link class="logo" v-bind:to="'/director/home'">
                            <img src="../../../../assets/images/logo-sm.png" alt="" height="50" class="logo-small" />
                            <img src="../../../../assets/images/logo.png" alt="" class="logo-large" />
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
                                    <i class="ti-bell noti-icon"></i>
                                    <span class="badge badge-danger noti-icon-badge">{{notificationCount.data.count}}</span>
                                </a>
                                <div class="dropdown-menu dropdown-menu-right dropdown-arrow dropdown-menu-lg">
                                    <!-- item-->
                                    <div class="dropdown-item noti-title">
                                        <h5>Notification</h5>
                                    </div>

                                    <!-- item-->

                                    <router-link v-bind:to="'/director/dirNotifications'" class="dropdown-item notify-item"
                                        v-for="notification in notification.data.list" :key="notification">
                                        <div class="notify-icon bg-primary"><i class="mdi mdi-account"></i></div>
                                        <p class="notify-details"><b>{{notification.title}}</b><small class="text-muted">{{notification.message}}</small></p>
                                    </router-link>



                                    <!-- All-->
                                    <router-link v-bind:to="'/director/dirNotifications'" class="dropdown-item notify-item">View
                                        All
                                    </router-link>
                                    <!-- All-->
                                    <router-link v-bind:to="'/director/dirSettings'" class="dropdown-item notify-item settings"><span class="fa fa-cog"></span>  Notifictions Settings
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
                                        <a class="dropdown-item" href="#"><i class="mdi mdi-account-circle m-r-5 text-muted"></i>
                                            {{profileData.data.profile.firstname}}</a>
                                        <div class="dropdown-divider"></div>
                                         <a style="cursor: pointer;" class="dropdown-item" v-on:click="logOut"><i class="mdi mdi-logout m-r-5 text-muted"></i>
                                            Logout</a>
                                    </div>
                                </div>
                            </li>
                            <li class="menu-item list-inline-item">
                                <!-- Mobile menu toggle-->
                                <a href="#menu-toggle" id="menu-toggle" class="navbar-toggle nav-link">
                                    <div class="lines">
                                        <span></span>
                                        <span></span>
                                        <span></span>
                                    </div>
                                </a>
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
                                <router-link v-bind:to="'/director/home'">
                                    <i class="mdi mdi-view-dashboard"></i>Dashboard
                                </router-link>
                            </li>

                            <li class="has-submenu">
                                <router-link v-bind:to="'/director/projects'">
                                    <i class="fa fa-users"></i>Projects
                                </router-link>
                            </li>


                            <li class="has-submenu ">
                                <router-link v-bind:to="'/director/profile'">
                                    <i class="fa fa-user"></i>My Profile
                                </router-link>

                            </li>

                            <li class="has-submenu">
                                <router-link v-bind:to="'/director/schedule'">
                                    <i class="mdi mdi-cards"></i>Auditions
                                </router-link>
                            </li>
                        </ul><!-- End navigation menu -->

                    </div> <!-- end #navigation -->
                </div> <!-- end container -->
            </div> <!-- end navbar-custom -->
        </header>
        <!-- End Navigation Bar-->
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'navHeader',
    methods: {
        logOut(){
            localStorage.removeItem('token');
            this.$router.push('/home');
            // this.$router.replace(this.$route.query.redirect || '/about')

        }
    },
    data(){
        return {
            loading: true,
            profileData: "",
            token: '',
            toggled: false,
            notificationCount: '',
            notification: '',
            siteUrl: "https://api.cast.i.ng/",
        };
    },
    mounted(){
        this.token = JSON.parse(localStorage.getItem('token'));
        console.log(this.token);

        this.loading = true;

        var config = {
            headers: {'Access-Control-Allow-Origin': '*'}
        };

        let userID = JSON.parse(localStorage.getItem('token'));
        // console.log(userID);

        axios({ method: "GET", "url": 'https://api.cast.i.ng/userdetails/'+userID , config }).then(result => {
            this.loading = false;
            this.profileData = result;
        }, error => {
            this.loading = false;
            console.log('API CALL FAILED');
            console.error(error);
        });

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
    }
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
</style>