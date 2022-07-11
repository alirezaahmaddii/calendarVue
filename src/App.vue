<template>
  <DayPilotCalendar id="dp" :config="config" ref="calendar" />

</template>


<script>
import {DayPilot, DayPilotCalendar} from '@daypilot/daypilot-lite-vue '

export default {
  name: 'Calendar',
  data: function() {
    return {
      config: {
        viewType: "Week",
        onTimeRangeSelected: (args) => {
          DayPilot.Modal.prompt("Create a new event:", "Event 1").then((modal) => {
            var dp = args.control;
            dp.clearSelection();
            if (modal.canceled) {
              return;
            }
            dp.events.add({
              start: args.start,
              end: args.end,
              id: DayPilot.guid(),
              text: modal.result
            });
          });
        },
        eventDeleteHandling: "Disabled",
        onEventMoved: () => {
          this.message("Event moved");
        },
        onEventResized: () => {
          this.message("Event resized");
        },
      },
    }
  },
  components: {
    DayPilotCalendar
  },
  computed: {
    calendar() {
      return this.$refs.calendar.control;
    }
  },
  methods: {
    loadEvents() {
      // placeholder for an AJAX call
      var data = [
        {
          id: 1,
          start: DayPilot.Date.today().addHours(10),
          end: DayPilot.Date.today().addHours(11),
          text: "Event 1"
        },
        {
          id: 2,
          start: DayPilot.Date.today().addHours(13),
          end: DayPilot.Date.today().addHours(16),
          text: "Event 2"
        }
      ];
      this.calendar.update({events: data});
    },
  },
  mounted() {
    this.loadEvents();
    this.calendar.message("Welcome!");
  }
}
</script>


<style lang="scss">

</style>