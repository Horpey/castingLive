<template>
  <div id="app">
    <styles/>
    <!-- @detected-condition fires when the connectivity status of the device changes -->
    <offline class="statusConnect" v-on:detected-condition="detected" @detected-condition="handleConnectivityChange" v-on:>
      <!-- Only renders when the device is online -->
      <div slot="online" class="connectStatus">
        <p>You are currently online</p>
      </div>
      <!-- Only renders when the device is offline -->
      <div slot="offline" class="connectStatus">
        <p>You appear to be offline, that's okay, we can still do things...</p>
      </div>
    </offline>
    <navheader v-show="$route.path != '/404'"/>
    <main>
      <router-view></router-view>
    </main>
    <!-- Add this v-show="$route.path != '/dashboard/home'" -->
    <siteFooter v-show="$route.path != '/404'"/>
  </div>
</template>

<script>
import navheader from './components/template/navheader';
import siteFooter from './components/template/siteFooter';
import offline from 'v-offline';
import Styles from './components/template/styles';

export default {
	name: 'app',
	components: {
		navheader: navheader,
		siteFooter: siteFooter,
    offline,
    styles: Styles,
  },
  data: function () {
    return {
      
      title: 'Casting',
      describ: 'Nigeria’s Number 1 premium casting website, for real actors by real casting directors. Powered by technology, with the aim of ease, efficiency and affordability.'
    }
  },
  methods: {
    handleConnectivityChange(status) {
      // console.log(status);
      if(!status){
        $( "#app" ).addClass( "grayscalePage" );
      }
      setTimeout(function(){ 
        $(".statusConnect").fadeOut();
       }, 3000);
    },
    detected(e) {
      this.state = e;
      setTimeout(function(){ 
        $(".statusConnect").fadeOut();
       }, 3000);
    }
  },
  mounted(){
    // if (location.protocol != 'https:')
    //   {
    //    location.href = 'https:' + window.location.href.substring(window.location.protocol.length);
    //   }
  }
  // Usage with context the component
  // head: {
  //   // To use "this" in the component, it is necessary to return the object through a function
  //   title: function () {
  //     return {
  //       inner: this.title
  //     }
  //   },
  //   meta: [
  //     { name: 'description', content: this.describ , id: 'desc' }
  //   ]
  // },

  // updated () {
  //   if (!localStorage.token && this.$route.path !== '/') {
  //     this.$router.push('/?redirect=' + this.$route.path)
  //   }
  // }
};
</script>

<style>
.connectStatus{
    position: fixed;
    z-index: 9999;
    width: 100%;
    text-align: center;
    bottom: 0;
    padding: 20px 0px;
}
.connectStatus p{
      margin-bottom: 0px;
    background-color: white;
    display: inline-block;
    padding: 12px 28px;
    border-radius: 36px;
    font-size: 15px!important;
    font-weight: bold;
    color: #e7077d;
    box-shadow: 0px 4px 7px #00000033;
}
.grayscalePage{
    -moz-filter: grayscale(100%);
    -webkit-filter: grayscale(100%);
    filter: gray; /* IE6-9 */
    filter: grayscale(100%);
}
</style>
