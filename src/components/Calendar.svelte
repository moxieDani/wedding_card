<script lang="ts">
	function getTdClass(index: number, day: number): string {
		let ret = '';
		if(index === 0 || index === 6)
			ret += 'ui-datepicker-week-end';
		if(day === 7)
			ret += ' ui-datepicker-days-cell-over ui-datepicker-current-day ui-state-active ui-state-hover';
		return ret;
	}
	function getDDay(): number {
		const year = 2024;
		const month = 9;
		const day = 7;
		const curDate: Date = new Date();
		const tarDate: Date = new Date(year, month - 1, day);
		const gap = tarDate.getTime() - curDate.getTime();
		return Math.ceil(gap / (1000 * 60 * 60 * 24));
	}
	let DDAY = getDDay();
	const daysOfWeek = ['S', 'M', 'T', 'W', 'T', 'F', 'Sa'];
	const weeks = [
		[1, 2, 3, 4, 5, 6, 7],
		[8, 9, 10, 11, 12, 13, 14],
		[15, 16, 17, 18, 19, 20, 21],
		[22, 23, 24, 25, 26, 27, 28],
		[29, 30, null, null, null, null, null]
	];
</script>

<section class="calendar-section">
	<div class="calendar-wrap">
		<div id="calendar" class="hasDatepicker">
			<div class="ui-datepicker" style="display: block;">
				<div class="ui-datepicker-header ui-widget-header ui-helper-clearfix ui-corner-all">
					<div class="ui-datepicker-title">
						<span class="ui-datepicker-month"><strong>9</strong>
						September</span>&nbsp;
						<span class="ui-datepicker-year">2024</span>
					</div>
				</div>
				<table class="ui-datepicker-calendar">
					<thead>
						<tr>
							{#each daysOfWeek as day, index}
								<th scope="col" class="{getTdClass(index, 0)}">
									<span title={day}>{day}</span>
								</th>
							{/each}
						</tr>
					</thead>
					<tbody>
						{#each weeks as week}
							<tr>
								{#each week as day, index}
									{#if day}
										<td class="{getTdClass(index, day)}" data-handler="selectDay" data-event="click">
											<a class="ui-state-default {getTdClass(index, day)}" href={'#'}>{day}</a>
										</td>
									{/if}
								{/each}
							</tr>
						{/each}
					</tbody>
				</table>

				{#if DDAY >= 0}
					<p class="flex-center" style="margin-top:6%; margin-bottom:5%;">{DDAY > 0 ? '결혼식까지 '+DDAY+'일 남았습니다.' : 'D-DAY!'}</p>
				{/if}
			</div>
		</div>
		<div class="day-time">
			<span class="day">토요일</span> <span class="time">pm 2:00</span>
		</div>
	</div>
</section>

<style>
table {
  width: 100%;
  border-collapse: collapse;
}
.calendar-section {
  padding: 1.250rem 1rem;
  background-color: #f4f4f4;
}
.calendar-wrap {
  position: relative;
}
.calendar-wrap .day-time {
  position: absolute;
  right: 1.563rem;
  top: 0.813rem;
  white-space: nowrap;
}

.calendar-wrap .day-time span {
  font-family: "campton";
  font-size: 0.875rem;
  line-height: 2.5rem;
  color: #111;
}

#calendar {
  background: #fff;
  border-radius: 10px;
  padding-bottom: 0.938rem;
}
.ui-datepicker-calendar thead,
.ui-datepicker-year{
	display:none;
}

.ui-datepicker{
	padding:0 1.250rem;
}
.ui-datepicker-header{
	margin:0 -1.250rem 0.938rem;
}
.ui-datepicker-title{
	padding:0.625rem 1.563rem 0;
	border-bottom:1px solid #eee;
}
.ui-datepicker-month{
	font-family:"campton";
	font-size:1.50rem;
	line-height:2.5rem;
}
.ui-datepicker-month strong{
	font-family:"campton";
	font-size:2.50rem;
	font-weight:bold;
}
.ui-datepicker-calendar{
	text-align:center;
	table-layout:fixed;
}
.ui-datepicker-calendar tbody td{
	padding:0.344rem;
	font-size:0;
	line-height:0;
	pointer-events:none;
}
.ui-datepicker-calendar tbody td span,
.ui-datepicker-calendar tbody td a{
	display:block;
	margin:0 auto;
	width:2.8125rem;
	height:2.8125rem;
	text-decoration:none;
	font-family:"campton";
	font-size:1.0rem;
	line-height:2.8125rem;
	color:#777;
	border:1px solid transparent;
	border-radius:50%;
}
.ui-datepicker-calendar tbody td.ui-datepicker-week-end:first-child span,
.ui-datepicker-calendar tbody td.ui-datepicker-week-end:first-child a{
	color:#ff6666;
}
.ui-datepicker-calendar tbody td.ui-datepicker-current-day span,
.ui-datepicker-calendar tbody td.ui-datepicker-current-day a{
	border-color:#000;
	background-color:#000;
	color:#fff !important;
}

</style>