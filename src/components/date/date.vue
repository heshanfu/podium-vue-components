<script>
  import Utils from './../../utils'
  import DateFilter from './../../filters/DateFormatFilter'

  const utils = Utils.Instance
  export default {
    name: 'pd-date',
    computed: {
      build () {
        const date = DateFilter(this.date, this.dateSettings.date)
        const time = DateFilter(this.date, this.dateSettings.time)
        let payload = ''
        if (this.showDate) {
          payload += date
        }
        if (this.showTime) {
          if (payload !== '') payload += ' '
          payload += time
        }
        return payload
      }
    },
    data () {
      return {
        dateSettings: utils.getDate()
      }
    },
    props: {
      date: {
        required: true,
        type: Date,
      },
      showTime: {
        required: false,
        default: true,
        type: Boolean,
      },
      showDate: {
        required: false,
        default: true,
        type: Boolean,
      }
    },
  }
</script>
<template lang="pug">
    span.pd-date(v-text='build')
</template>
