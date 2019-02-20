<template>
    <span v-if="showTimeString">{{timeString}}</span>
</template>

<script>
    export default {
        name: 'clocker',
        props: {
            showTimeString:{
                type: Boolean,
                default: true
            },
            doStart:{
                type: Boolean,
                default: false
            },
            format: {
                type: String,
                default: 'hh:mm:ss'
            }
        },
        watch:{
            doStart(val){
                if(val){
                    this.startTime()
                }
            }
        },
        data() {
            return{
                timeString: '',
                startDate:'',
                finalDate:''
            }
        },
        methods:{
            startTime () {
                if(this.doStart){
                    this.startDate = new Date()
                    if (this.interval !== null) {
                        clearInterval(this.interval)
                    }
                    let self = this
                    this.update()
                    this.interval = setInterval(function () {
                        self.update()
                    }, 100)
                    return this
                }
            },
            finishTime () {
                this.doStart = false
                if (this.interval !== null) {
                    clearInterval(this.interval)
                }
                return this.timeString
            },
            getOffset () {
                this.totalSecsLeft = new Date().getTime() - this.startDate.getTime() // In miliseconds
                this.totalSecsLeft = Math.ceil(this.totalSecsLeft / 1000)
                this.totalSecsLeft = this.totalSecsLeft < 0 ? 0 : this.totalSecsLeft
                // Calculate the offsets
                return {
                    seconds: this.totalSecsLeft % 60,
                    minutes: Math.floor(this.totalSecsLeft / 60) % 60,
                    hours: Math.floor(this.totalSecsLeft / 60 / 60) % 24,
                    days: Math.floor(this.totalSecsLeft / 60 / 60 / 24),
                    weeks: Math.floor(this.totalSecsLeft / 60 / 60 / 24 / 7),
                    months: Math.floor(this.totalSecsLeft / 60 / 60 / 24 / 30),
                    years: Math.floor(this.totalSecsLeft / 60 / 60 / 24 / 365)
                }
            },
            splitNumber (number) {
                return number = (number < 10 ? ('0' + number) : number)
            },
            update () {
                // Calculate the offsets
                const offset = this.getOffset()
                this.timeString = this.format.replace(/yy/,this.splitNumber(offset.years))
                    .replace(/MM/,this.splitNumber(offset.months))
                    .replace(/dd/,this.splitNumber(offset.days))
                    .replace(/hh/,this.splitNumber(offset.hours))
                    .replace(/mm/,this.splitNumber(offset.minutes))
                    .replace(/ss/,this.splitNumber(offset.seconds))
                return this
            },
        }
    }
</script>