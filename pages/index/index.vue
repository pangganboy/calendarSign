<template>
	<view class="content">
		<ren-calendar ref='ren' :collapsible='false' :weekstart='1' :disabledAfter="true" :markDays='markDays'
			:headerBar='true' @onDayClick='onDayClick'></ren-calendar>
		<button @click="workSign">签到</button>
	</view>
</template>

<script>
	import RenCalendar from '@/components/ren-calendar/ren-calendar.vue'
	export default {
		components: {
			RenCalendar
		},
		data() {
			return {
				curDate: '',
				markDays: []
			}
		},
		onReady() {
			let today = this.$refs.ren.getToday();
			this.curDate = today;
			// this.markDays.push(today);
		},
		methods: {
			onDayClick(data) {
				this.curDate = data;
				this.markDays.push(this.curDate);
				console.log(this.markDays)
			},
			workSign() {
				let flat = false;
				this.markDays.forEach(item => {
					 if(item.date == this.curDate.date){
						 console.log(item.date,this.curDate.date)
						flat = true 
					 }
				})
				console.log(flat)
				let flat1 = this.markDays.map(item => {
					if (item.date == this.curDate.date) {
						return true
					}
				})
				// if (this.markDays.indexOf(this.curDate) > -1) return;
				// this.markDays.push(this.curDate);
			}
		}
	}
</script>

<style>

</style>
