<template>
  
</template>

<script>
import i18n from '../i18n.js'
import { dateTimeFormatter } from '../tools.js'
import calEventItem from './cal-event-item.vue'
export default {
  name: 'cal-events',
  data () {
    return {
      i18n
    }
  },
  components: {
    'cal-event-item': calEventItem
  },
  props: {
    dayEvents: {
      type: Object,
      required: true
    },
    locale: {
      type: String,
      required: true
    },
    color: {
      type: String,
      required: true
    }
  },
  computed: {
    dayEventsTitle () {
      if (this.dayEvents.date !== 'all') {
        if (this.dayEvents.events.length !== 0) {
          let tempDate = Date.parse(new Date(this.dayEvents.events[0].date))
          return dateTimeFormatter(tempDate, i18n[this.locale].fullFormat)
        } else {
          return this.dayEvents.date + i18n[this.locale].notHaveEvents
        }
      } else {
        return i18n[this.locale].dayEventsTitle
      }
    },
    events () {
      return this.dayEvents.events
    },
    bgColor () {
      return {backgroundColor: this.color}
    }
  },
  methods: {
    dateTimeFormatter
  }
}
</script>
