<template>
  <div>
  <HotelDatePicker 
  :format="DatePicker.formatDate"
  :disabledDaysOfWeek="DatePicker.disableDays"
  :startDate="startDay()"
  :endDate="endDay()"
  :displayClearButton="false"
  :gridStyle="true"
  :i18n=" DatePicker.ptBr"
  :disabledDates="DatePicker.disabledDates"
  :lastDateAvailable="DatePicker.lastDateAvailable"
  @check-in-changed="setCheckinDate"
  @check-out-changed="setCheckoutDate"
  />
  </div>

</template>
<script>
import HotelDatePicker from 'vue-hotel-datepicker';
import 'vue-hotel-datepicker/dist/vueHotelDatepicker.css';
export default {
  components: {
   HotelDatePicker 
  },
   data(){
    return{
      DatePicker:{
        formatDate:'YYYY/MM/DD',
        disableDays:[],
        disabledDates:[ ],
        startDay:'',
      /* ptBr: {
        night: 'Noite',
        nights: 'Noites',
       'day-names': ['Dom', 'Seg', 'Ter', 'Qua', 'Qui', 'Sex', 'Sab'],
       'check-in': 'Chegada',
       'check-out': 'Partida',
       'month-names': ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio', 'Junho', 'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'],
       }, */
      }
    }
  },
  methods: {
    startDay() {
    var now = new Date();
    return new Date(now.getFullYear()-11, now.getMonth()+3, 1);
  },
  endDay(){
     return new Date(new Date().getFullYear(), 10, 31)
  },
  setCheckinDate(fromDay) {
        this.fromDay=fromDay;
  },
  setCheckoutDate(toDay) {
    if(toDay !== null){
    console.log("START DAY IS :" , this.fromDay);
    console.log("END DAY IS :" , toDay);
    }
    
        
    },
},
}
</script>
