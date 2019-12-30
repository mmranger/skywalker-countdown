<template>
    <div class="wrapper">
        <div class="time">
            {{ days | beautify }}
            <div class="time__mode">
                Days
            </div>
        </div>
        <div class="time">
            {{ hours | beautify }}
            <div class="time__mode">
                Hours
            </div>

        </div>
        <div class="time">
            {{ minutes| beautify }}
            <div class="time__mode">
                Minutes
            </div>

        </div>
        <div class="time">
            {{ seconds | beautify }}
            <div class="time__mode">
                Seconds
            </div>

        </div>

    </div>
</template>
<style>
    .wrapper {
        width: 100%;
        position: absolute;
        transform: translate(-50%, -50%);
        -ms-transform: translate(-50%, -50%);
        -webkit-transform: translate(-50%, -50%);
        -moz-transform: translate(-50%, -50%);
        -o-transform: translate(-50%, -50%);
        top: 10%;
        left: 50%;
        dislpay: inline-block;
        text-align: center;
        font-family: "Lato", Arial, sans-serif;
        font-weight: normal;
        color: #d70000;
    }

    .time {
        display: inline-block;
        padding: 20px;
        font-size: 7em;
        font-weight: 700;
        text-shadow: 0px 5px 20px rgba(0,0,0,0.7)
    }

    @media screen and (max-width: 768px) {
        .time {
            font-size: 2em;
        }
    }

    .time .time__mode {
        font-size: 25px;
        font-weight: 300;
        margin: 7px 0;
        letter-spacing: 4px;
        text-shadow: 0px 4px 14px rgba(0,0,0,0.5)
    }

    @media screen and (max-width: 768px) {
        .time .time__mode {
            font-size: 12px;
            letter-spacing: normal;
        }
    }
</style>
<script>
import moment from 'moment'
export default{
  props: ['dateProps'],
  mounted: function () {
    this.$nextTick(function () {
      window.setInterval(() => {
        this.current = Math.trunc((new Date()).getTime() / 1000)
      },
      1000
      )
    })
  },
  data () {
    return {
      current: Math.trunc((new Date()).getTime() / 1000),
      date: Math.trunc(Date.parse(this.calculateCountdownDay()) / 1000)
    }
  },
  methods: {
    calculateCountdownDay () {
      // Code to check that date and dayOfWeek are valid left as an exercise ;)
      var dayOfWeek = 5 // Friday = 5
      var hourOfDay = '3:00' // in military time?
      var date = new Date()
      var fridayDate
      var fridayYear
      console.log('Date: ' + date)
      var resultDate = new Date(date.getTime())
      // console.log('resultDate: ' + resultDate)
      // console.log('GetDay(): ' + date.getDay())
      // console.log('with mod: ' + moment(resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) % 7)).format('MMMM DD'))
      // console.log('with out mod: ' + moment(resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) / 7)).format('MMMM DD'))
      // console.log('resultDate calculated: ' + moment(resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) % 7)).format('MMMM DD'))
      // console.log('resultDate calculated: ' + resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) % 7))
      if (date.getDay() === dayOfWeek) {
        fridayDate = moment(resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) % 7 + 7)).format('MMMM DD')
        fridayYear = moment(resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) % 7 + 7)).format('YYYY')
        console.log('today is friday?')
      } else {
        fridayDate = moment(resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) % 7)).format('MMMM DD')
        fridayYear = moment(resultDate.setDate(date.getDate() + (7 + dayOfWeek - date.getDay()) % 7)).format('YYYY')
        console.log('today is any day but friday?')
      }
      // var fridayHour = moment(resultDate.setDate(date.getHours() + (24 + hourOfDay - date.getHours()) % 24)).format('HH:MM')

      // return moment(resultDate).format('MMMM Do YYYY').toString()
      // return resultDate
      console.log(fridayDate + ', ' + fridayYear + ' ' + hourOfDay)
      return fridayDate + ', ' + fridayYear + ' ' + hourOfDay
    }
  },

  computed: {
    days () {
      return Math.trunc((this.date - this.current) / 3600 / 24)
    },

    hours () {
      return Math.trunc((this.date - this.current) / 3600) % 24
    },

    minutes () {
      return Math.trunc((this.date - this.current) / 60) % 60
    },

    seconds () {
      return Math.trunc((this.date - this.current)) % 60
    }
  },

  filters: {
    beautify: function (value) {
      let temp = value.toString()

      if (temp.length <= 1) {
        return '0' + value.toString()
      } else {
        return value.toString()
      }
    }
  }
}
</script>
