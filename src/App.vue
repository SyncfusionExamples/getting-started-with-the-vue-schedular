<template>
<div id='app'>
  <ejs-schedule height="550px" currentView="Month" 
  :eventSettings="appointmentData">
  </ejs-schedule>
  <!-- <ejs-schedule height="550px" currentView="Month" :selectedDate="schedulerSelectedDate" 
  :eventSettings="appointmentData">
  </ejs-schedule> -->
</div>
</template>

<script> 
import { ScheduleComponent, Day, Week, WorkWeek, Month, Agenda } from "@syncfusion/ej2-vue-schedule";
import { DataManager, WebApiAdaptor } from "@syncfusion/ej2-data"; 

var remoteData= new DataManager({
  url : 'https://ej2services.syncfusion.com/production/web-services/api/Schedule',
  adaptor : new WebApiAdaptor,
  crossDomain : true
});

export default {
  name: 'App',
  components: {
    'ejs-schedule': ScheduleComponent
  },
  provide : {
    schedule : [Day, Week, WorkWeek, Month, Agenda]
  },
  data() {
    return {
     // schedulerSelectedDate : new Date(2022, 4, 12),
      appointmentData : {
        dataSource : remoteData
        // dataSource : [
        //     {
        //      Subject : 'Project Meeting',
        //      StartTime: new Date(2022, 4, 10, 9, 0),
        //      EndTime: new Date(2022, 4, 10, 10, 0)
        //    },
        //    {
        //      Subject : 'Review Meeting',
        //      StartTime: new Date(2022, 4, 11, 10, 0),
        //      EndTime: new Date(2022, 4, 11, 11, 30),
        //      IsReadonly : true
        //    },
        //    {
        //      Subject : 'Status Meeting',
        //      StartTime: new Date(2022, 4, 12, 11, 30),
        //      EndTime: new Date(2022, 4, 12, 12, 30)
        //    }
        // ]
      }
    };
  },
}
</script>

<style>
@import '../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';
</style>
