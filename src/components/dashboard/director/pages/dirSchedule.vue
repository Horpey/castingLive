<template>
    <div>
        <loader v-if="loading"/>
        <div class="card m-b-30">
            <div class="card-body">
                <p class="cv1">
                    <b class="col-ppd">Audition Events</b>

                    <router-link v-bind:to="'/director/projects'" class="mdb float-right text-white" style="cursor: pointer;">Add Event
                                </router-link>

                </p>

                 <div style="margin-top: 12px;" class="alert" v-bind:class="{ success: status, danger: !status }" v-if="error">{{ error }}</div>

                <table class="table table-striped mb-0">
                    <tbody>
                        <tr>
                            <!-- <td>S/N</td> -->
                            <td><b>Date</b></td>
                            <td><b>Address</b></td>
                            <td><b>Time</b></td>
                            <td><b>Invited</b></td>
                            <td><b>Status</b></td>
                            <td><b>Action</b></td>
                        </tr>

                    </tbody>
                    <tbody>
                        <tr v-for="(schedule, index) in scheduleData.data.list">
                            <!-- <td>{{index+1}}</td> -->
                            <td>{{schedule.date | moment().format("DD MMM YYYY") }}</td>
                            <td>{{schedule.address}}</td>
                            <td>{{schedule.time }}</td>
                            <td>{{schedule.invited}}</td>
                            <td>Invited</td>
                            <td>
                                <div class="dropdown">
                                    <button class="btn btn-secondary dropdown-toggle" type="button" data-toggle="dropdown">
                                        Action
                                        <span class="caret"></span>
                                    </button>
                                    <div id="pos">
                                        <ul class="dropdown-menu">
                                            <li>
                                                <a style="cursor: pointer;" v-on:click="deleteSchedule(schedule.id)" class="dropdown-item" >Delete</a>
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </td>
                        </tr>                     
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import Loader from '../template/loader';
export default {
    name: 'dirSchedule',
    data() {
        return {
            loading: true,
            scheduleData: "",
            token: '',
            scheduleMsg: '',
            error: '',
            siteUrl: "https://api.cast.i.ng/",
        };
    },
    components: {
        loader: Loader,
    },
    mounted() {

        this.token = JSON.parse(localStorage.getItem('token'));
        console.log(this.token);

        this.loading = true;

        var config = {
            headers: {'Access-Control-Allow-Origin': '*'}
        };

        let userID = JSON.parse(localStorage.getItem('token'));
        // console.log(userID);

        axios({ method: "GET", "url": 'https://api.cast.i.ng/director/events/'+userID , config }).then(result => {
            this.loading = false;
            this.scheduleData = result;
        }, error => {
            this.loading = false;
            console.log('API CALL FAILED');
            console.error(error);
        });


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

    methods: {
        deleteSchedule(scheduleID){
            var sureDelete = confirm('Are you sure you want to delete??');
            if(sureDelete){
                var config = {
                    headers: { 'Access-Control-Allow-Origin': '*' },
                };

                axios({ method: 'GET', url: 'https://api.cast.i.ng/delete/event/' + scheduleID, config }).then(
                    result => {
                        this.loading = false;
                        this.scheduleMsg = result;
                        this.error = result.data.status_msg;
                        location.reload();
                        // this.$router.replace(this.$route.query.redirect || '/dashboard/profile');
                    },
                    error => {
                        this.loading = false;
                        console.log('API CALL FAILED');
                        // this.$router.replace(this.$route.query.redirect || '/dashboard/profile');
                        console.error(error);
                        this.error = 'Failed to Delete';
                    }
                );

            }
            
        }
    }
};
</script>

<style>

.form-loader {
        width: 22px;
    }

    .success {
        color: #155724;
        background-color: #d4edda;
        border-color: #c3e6cb;
    }

    .danger {
        color: #721c24;
        background-color: #f8d7da;
        border-color: #f5c6cb;
    }

</style>