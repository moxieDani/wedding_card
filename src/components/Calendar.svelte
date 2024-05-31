<script lang="ts">
	function getDDay(year: number, month: number, day: number): number {
		const curDate: Date = new Date();
		const tarDate: Date = new Date(year, month - 1, day);
		const gap = tarDate.getTime() - curDate.getTime();
		return Math.ceil(gap / (1000 * 60 * 60 * 24));
	}
	const DDAY = getDDay(2024, 9, 7);
</script>

<section class="calendar-section">
	<div class="calendar-wrap">
		<div id="calendar" class="hasDatepicker">
			<div class="ui-datepicker-inline ui-datepicker ui-widget ui-widget-content ui-helper-clearfix ui-corner-all"
				style="display: block;">
				<div class="ui-datepicker-header ui-widget-header ui-helper-clearfix ui-corner-all">
					<div class="ui-datepicker-title"><span class="ui-datepicker-month"><strong>9</strong>
							September</span>&nbsp;<span class="ui-datepicker-year">2024</span></div>
				</div>
				<table class="ui-datepicker-calendar">
					<thead>
						<tr>
							<th scope="col" class="ui-datepicker-week-end"><span title="일요일">S</span></th>
							<th scope="col"><span title="월요일">M</span></th>
							<th scope="col"><span title="화요일">T</span></th>
							<th scope="col"><span title="수요일">W</span></th>
							<th scope="col"><span title="목요일">T</span></th>
							<th scope="col"><span title="금요일">F</span></th>
							<th scope="col" class="ui-datepicker-week-end"><span title="토요일">Sa</span></th>
						</tr>
					</thead>
					<tbody>
						<tr>
							<td class=" ui-datepicker-week-end" data-handler="selectDay" data-event="click"
									data-month="9" data-year="2024"><a class="ui-state-default" href="#">1</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">2</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">3</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">4</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">5</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">6</a></td>
							<td class=" ui-datepicker-week-end ui-datepicker-days-cell-over  ui-datepicker-current-day"
								data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default ui-state-active ui-state-hover" href="#">7</a></td>
						</tr>
						<tr>
							<td class=" ui-datepicker-week-end " data-handler="selectDay" data-event="click"
								data-month="9" data-year="2024"><a class="ui-state-default" href="#">8</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">9</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">10</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">11</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">12</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">13</a></td>
							<td class=" ui-datepicker-week-end " data-handler="selectDay" data-event="click"
								data-month="9" data-year="2024"><a class="ui-state-default" href="#">14</a></td>
						</tr>
						<tr>
							<td class=" ui-datepicker-week-end " data-handler="selectDay" data-event="click"
								data-month="9" data-year="2024"><a class="ui-state-default" href="#">15</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">16</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">17</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">18</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">19</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">20</a></td>
							<td class=" ui-datepicker-week-end " data-handler="selectDay" data-event="click"
								data-month="9" data-year="2024"><a class="ui-state-default" href="#">21</a></td>
						</tr>
						<tr>
							<td class=" ui-datepicker-week-end " data-handler="selectDay" data-event="click"
								data-month="9" data-year="2024"><a class="ui-state-default" href="#">22</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">23</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">24</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">25</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">26</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">27</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">28</a></td>
						</tr>
						<tr>
							<td class=" ui-datepicker-week-end " data-handler="selectDay" data-event="click"
								data-month="9" data-year="2024"><a class="ui-state-default" href="#">29</a></td>
							<td class=" " data-handler="selectDay" data-event="click" data-month="9" data-year="2024"><a
									class="ui-state-default" href="#">30</a></td>
							<td class=" ui-datepicker-other-month ui-datepicker-unselectable ui-state-disabled">&nbsp;
							</td>
							<td
								class=" ui-datepicker-week-end ui-datepicker-other-month ui-datepicker-unselectable ui-state-disabled">
								&nbsp;</td>
						</tr>
					</tbody>
				</table>
				{#if DDAY >= 0}
					<p class="flex-center">{DDAY > 0 ? '결혼식까지 '+DDAY+'일 남았습니다.' : 'D-DAY!'}</p>
				{/if}
			</div>
		</div>
		<div class="day-time">
			<span class="day">토요일</span> <span class="time">pm 2:00</span>
		</div>
	</div>
</section>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* 화면 전체 높이 */
}

.table-wrapper {
  width: 80%; /* 화면 너비의 80% */
  max-width: 1200px; /* 최대 너비 1200px */
}

table {
  width: 100%; /* 테이블 너비 100% */
  border-collapse: collapse; /* 테두리 병합 */
}
.contain {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* 화면 전체 높이 */
}

.tb {
  width: 100%;
  max-width: 800px; /* 최대 너비 설정 */
}

.ib {
  display: block;
  width: 100%;
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
.ui-datepicker-year,
.ui-datepicker-prev,
.ui-datepicker-next{
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