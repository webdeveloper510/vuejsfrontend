<template>
  <div data-v-3e2a69a8="" class="form-builder--heading">
         <div data-v-3e2a69a8="" class="form-builder--heading__options">
            <div data-v-3e2a69a8="" class="form-builder--heading__tabs">
               <div data-v-3e2a69a8="" class="sh-tabs">
                  <ul data-v-3e2a69a8="" style="border-bottom: none; position: relative; bottom: -1px;">
                     <li data-v-3e2a69a8=""><a data-v-3e2a69a8="" href="#" class="">Forms</a></li>
                     <li data-v-3e2a69a8=""><a data-v-3e2a69a8="" href="#" class="is-active">Submissions</a></li>
                     <li data-v-3e2a69a8=""><a data-v-3e2a69a8="" href="#" class="">Reports</a></li>
                  </ul>
               </div>
            </div>
            <div data-v-3e2a69a8="" class="form-builder--heading__options-right">
               <div data-v-3e2a69a8="">
                  <div data-v-3e2a69a8="" class="has-text-right is-medium-14-500-24">Setting</div>
               </div>
            </div>
         </div>
         <div class=" text-left">
            <div class="">
               <a class="subbutton" href="#" @click="shared_with_me()"> Shared with me</a>
               <a class="subbutton" href="#" @click="my_submission()"> My Submission</a>
               <!-- <a class="subbutton" href="#"> Other Submitations</a> -->
            </div>
         </div>
         
         <div class="row buttonsbar">
            <div class="col-md-3">
               <form class="form-inline my-2 my-lg-0">
                  <i class="fa fa-search searchicon"></i> <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
                 
               </form>
               
            </div>
            <div class="col">
                <i class="fa fa-filter"></i>
            </div>
            <div class="col-md-4">

            </div>
    
            <div class="col-md-4">
               Show:
               <select class="custom-select" id="inputGroupSelect01">
                  <option selected>All Time</option>
                  <option value="1">One</option>
                  <option value="2">Two</option>
                  <option value="3">Three</option>
               </select>
               Group By:
               <select class="custom-select" id="inputGroupSelect01">
                  <option selected>None</option>
                  <option value="1">One</option>
                  <option value="2">Two</option>
                  <option value="3">Three</option>
               </select>
            </div>
         </div>
           <div class="tickets-main-section--columns is-vcenter">
        <submission-header :small_viewer="is_vertical_window" :sorting_key="sort_key" @update_sort_key="sort_key = $event"></submission-header>
      </div>
     <div v-if="SharedWithMe.length"> 
       <div  v-for="sharedwithme in SharedWithMe" :key="sharedwithme.id">
                <submission-list
                  :submission="sharedwithme"
                  :is_vertical_window="is_vertical_window"
                ></submission-list>
                
                
              </div>
              </div>
  </div>
</template> 
<script>
import {submissions} from "@/desktop/forms/services/controller/submissions.js";
import SubmissionHeader from "@/desktop/forms/components/submission/component/submission-header";
import SubmissionList  from "@/desktop/forms/components/submission/component/submission-list";
  export default {
     SharedWithMe:null,
     components:{
        SubmissionHeader,
        SubmissionList
     },
     created(){

        this.sharedWithMe()
     },  
    methods: {
       async sharedWithMe(){
       let query= "&owner=true" + "&status=pending" +"&organization=00gkgsfp9gz5LJvhQ0h7";
       let header ="token  "+ window.$cookies.get("access_token");
         let {data} = await submissions.get({query , header}).catch((err) => this.handleErrors());
         
         this.SharedWithMe=data.data
         console.log("data coming",this.SharedWithMe)
      }
    },
  };
</script>
<style lang="scss">
   .row.buttonsbar {
   float: left;
   width: 100%;
   margin-top: 16px;
   }
   input.form-control.mr-sm-2 {
   height: 39px;
   border: 2px solid white;
   font-size: 17px;
   margin-right: 19px;
   }
   i.fa.fa-filter {
   background: white;
   padding: 13px;
   box-shadow: 1px 2px 3px 1px #a49b9bb5;
   }
   select#inputGroupSelect01 {
   border: none;
   background: transparent;
   margin-right: 35px;
   }
   i.fa.fa-search.searchicon {
    margin-left: 10px;
    margin-right: 10px;
}
   form.form-inline.my-2.my-lg-0 {
    box-shadow: 1px 2px 3px 1px #a49b9bb5;
    padding: 7px;
}
a.subbutton {
   border: 1px solid black;
   padding: 8px;
   background: white;
   color: black;
   margin-left: 11px;
   border-radius: 21px;
   }
</style>
