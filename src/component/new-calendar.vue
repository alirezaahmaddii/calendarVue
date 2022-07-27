<template>
<div>
  <FullCalendar :options="calendarOptions"   />
</div>
</template>

<script>
import '@fullcalendar/core/vdom'
import FullCalendar from '@fullcalendar/vue3'
import dayGridPlugin from '@fullcalendar/daygrid'
import interactionPlugin from '@fullcalendar/interaction'
import list from '@fullcalendar/list'
import bootstrap5 from '@fullcalendar/bootstrap5'
// import bootstrap4 from '@fullcalendar/bootstrap'
import timegrid from '@fullcalendar/timegrid'
export default {
  components:{
    FullCalendar
  },
  data:()=>({
    calendarOptions: {
      plugins: [ dayGridPlugin, interactionPlugin, list,bootstrap5,timegrid ],
      initialView: 'dayGridMonth',
      themeSystem: 'bootstrap5',
      // dateClick:this.handleDateClick,
      selectable: true,

      events: [
        { title: 'event 1', date: '2022-07-24' },
        { title: 'event 2', date: '2022-07-28' },
        { title: 'event 3', date: '2022-07-04' },
      ],
      // views: {
      //   dayGridMonth: { buttonText: "month" },
      //   timeGridWeek: { buttonText: "week" },
      //   timeGridDay: { buttonText: "day" },
      // },
      height: 850,
      contentHeight: 780,
      // aspectRatio: 3,
      // nowIndicator: true,
      editable: true,
      // navLinks:false,
      headerToolbar:{
        left:'',
        center: 'title',
        right:'dayGridMonth timeGridWeek list'
      },

    },
    purchase: {
      title: 'event 4',
      date: '2022-07-05',
    },
  }),
  methods: {
    add(){
      console.log(1)
      this.calendarOptions.events.push(this.purchase)
    },
    pupup(){
      let box = document.querySelector('td')
        box.addEventListener('click',function (){
          alert('sdf');
        })
    }
  },
  mounted() {
    this.add()
    this.pupup()
  }

}
</script>

<style lang="scss">
.btn-check:active + .btn-primary, .btn-check:checked + .btn-primary, .btn-primary.active, .btn-primary:active, .show > .btn-primary.dropdown-toggle{
  background-color: #EFF2F5 !important;
  color: black !important;
  border: 1px solid #EFF2F5 !important;
  box-shadow: unset !important;
  box-shadow: 0 0 3px #696363 !important;
}
.btn-primary{
  color: #000000 !important;
    background-color: #F5F8FA !important;
  border: 1px solid #F5F8FA !important;
}
</style>