<template>
  <div>
    <!--  -->
    <full-calendar class="test-fc" 
        :options="calendarOptions" 
        :initialTimeFrame="'day'" 
        first-day='1'
        locale="en"
        @changeMonth="changeMonth" 
        @eventClick="eventClick" 
        @dayClick="dayClick" 
        @moreClick="moreClick">
      
    </full-calendar>
  </div>
</template>
<script>
import moment from 'moment'

const options = {
  dayStartTime: '8:00am', // Start time on the calendar
  dayEndTime: '5:30pm', // End time on the calendar
  weekLength: 5, // or 7 
  colors: ['3498DB', 'F1C40F', 'E74C3C', '1ABC9C'],
  dayButtonClass: 'btn btn-secondary', // TODO: figure out if this should be in a header obj
  weekButtonClass: 'btn btn-secondary',
  monthButtonClass: 'btn btn-secondary',
  // rightArrow: '',
  leftArrow: '◀',
  resources: {
    groups: [ //Split resources into different related groups
      {
        type: 'people', // The type of resource
        resourceNames: ['Charity Barnum', 'Rhett Butler', 'Annie Oakley', 'Dorothy Gale'], //All potential resources in this group
        events: [ //The events for this resource group. The resourceName should map to something in resourceNames
          {
            resourceName: 'Charity Barnum',
            date: moment().format('YYYY-MM-DD'), // '2017-08-08',
            startTime: '12:00pm', //Start time should always be there
            endTime: '4:30pm', //End time is optional, should be able to figure this out from the duration if it's included instead
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client',
            color: 'FFF',
            textColor: 'ff0000'
          }, {
            resourceName: 'Charity Barnum',
            date: moment().format('YYYY-MM-DD'),
            startTime: '8:00am', //Start time should always be there
            duration: '3.75', //End time is optional, should be able to figure this out from the duration if it's included instead
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client'
          }, {
            resourceName: 'Rhett Butler',
            date: moment().format('YYYY-MM-DD'),
            startTime: '8:00am',
            duration: '3.75', // this should be time format (h:mm) or decimal (3.75 (3:45 === 3.75)) TODO: or minutes (probably best)
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client1'
          }, {
            resourceName: 'Annie Oakley',
            date: moment().format('YYYY-MM-DD'),
            startTime: '3:00pm',
            duration: '145', // minutes
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client1'
          }, {
            resourceName: 'Charity Barnum',
            date: moment().subtract(1, 'd').format('YYYY-MM-DD'), // '2017-08-08',
            startTime: '12:00pm', //Start time should always be there
            endTime: '4:30pm', //End time is optional, should be able to figure this out from the duration if it's included instead
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client',
            color: 'FFF'
          }, {
            resourceName: 'Charity Barnum',
            date: moment().subtract(1, 'd').format('YYYY-MM-DD'),
            startTime: '8:00am', //Start time should always be there
            duration: '3.75', //End time is optional, should be able to figure this out from the duration if it's included instead
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client'
          }, {
            resourceName: 'Rhett Butler',
            date: moment().subtract(1, 'd').format('YYYY-MM-DD'),
            startTime: '8:00am',
            duration: '3.75', // this should be time format (h:mm) or decimal (3.75 (3:45 === 3.75)) TODO: or minutes (probably best)
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client1'
          }
        ]
      }, {
        type: 'contractors',
        resourceNames: ['Contractor One', 'Contractor Two'],
        events: []
      }, {
        type: 'machine',
        resourceNames: ['Machine Two', 'Machine Three', 'Machine Four'],
        events: [
          {
            resourceName: 'Machine One',
            date: moment().format('YYYY-MM-DD'),
            startTime: '1:00pm', //Start time should always be there
            endTime: '4:00pm', //End time is optional, should be able to figure this out from the duration if it's included instead
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'pm'
          }, {
            resourceName: 'Machine One',
            date: moment().format('YYYY-MM-DD'),
            startTime: '8:00am', //Start time should always be there
            endTime: '11:00am', //End time is optional, should be able to figure this out from the duration if it's included instead
            type: 'Job am',
            title: 'Manufacture Workspace',
            recipient: 'am'
          }, {
            resourceName: 'Machine Two',
            date: moment().format('YYYY-MM-DD'),
            startTime: '8:00am',
            duration: '3:45', // TODO: decide whether this should be time format (h:mm) or decimal (3.75 (3:45 === 3.75)) or minutes (probably best)
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client1'
          }, {
            resourceName: 'Machine Four',
            date: moment().format('YYYY-MM-DD'),
            startTime: '3:00pm',
            duration: '120', // minutes
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client1'
          }, {
            resourceName: 'Machine Two',
            date: moment().format('YYYY-MM-DD'),
            startTime: '11:30am',
            duration: '3:45', // TODO: decide whether this should be time format (h:mm) or decimal (3.75 (3:45 === 3.75)) or minutes (probably best)
            type: 'Job',
            title: 'Manufacture Workspace',
            recipient: 'Client2'
          }
        ]
      }
    ]
  }
}

export default {
  data() {
    return {
      name: 'Sunny!',
      calendarOptions: options
    }
  },
  methods: {
    'changeMonth'(start, end, current) {
      console.log('changeMonth', start.format(), end.format(), current.format())
    },
    'eventClick'(event, jsEvent, pos) {
      console.log('eventClick', event, jsEvent, pos)
    },
    'dayClick'(day, jsEvent) {
      console.log('dayClick', day, jsEvent)
    },
    'moreClick'(day, events, jsEvent) {
      console.log('moreCLick', day, events, jsEvent)
    }
  },
  components: {
    'full-calendar': require('src/fullCalendar')
  }
}
</script>
<style lang='scss'>
.app {
  color: green;
  font-family: Arial, Helvetica, sans-serif;
}
</style>