<script lang="ts">
  function getTdClass(index: number, day: number): string {
    let ret = '';
    if(index === 0 || index === 6)
      ret += 'datepicker-week-end';
    if(day === 7)
      ret += ' datepicker-days-cell-over datepicker-current-day state-active state-hover';
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
    <div id="calendar" class="hasDatepicker datepicker" style="display: block;">
      <div class="datepicker-header widget-header helper-clearfix corner-all">
        <div class="datepicker-title">
          <span class="datepicker-month"><strong>9</strong> September</span>&nbsp;
          <span class="datepicker-year">2024</span>
        </div>
      </div>
      <div class="day-time">
        <span class="day">토요일</span> <span class="time">pm 2:00</span>
      </div>
      <table class="datepicker-calendar">
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
                    <span class="state-default {getTdClass(index, day)}">{day}</span>
                  </td>
                {/if}
              {/each}
            </tr>
          {/each}
        </tbody>
      </table>

      {#if DDAY >= 0}
        <p class="d-day">
          기순<span class="heart">&nbsp;♥&nbsp;</span>서은의 결혼식이
          {#if DDAY > 0}
            {DDAY}일 남았습니다.
          {:else}
            오늘입니다!
          {/if}
        </p>
      {/if}
    </div>
  </div>
</section>
<style>
table {
  width: 100%;
  border-collapse: collapse;
}
.calendar-section {
  padding: 1.25rem 1rem;
  background-color: #f8f9fa;
}
.calendar-wrap {
  position: relative;
}
.calendar-wrap .day-time {
  position: absolute;
  padding-top: 4%;
  margin-right: 1%;
  right: 1.563rem;
  top: 0.813rem;
  white-space: nowrap;
  font-family: "campton";
  font-size: 1.2rem;
  line-height: 2.5rem;
  color: #111;
}
#calendar {
  background: #fff;
  border-radius: 10px;
  padding-bottom: 0.938rem;
  padding: 0 1.25rem;
}
.datepicker-header {
  margin: 0 -1.25rem 0.938rem;
}
.datepicker-title {
  padding: 0.625rem 1.563rem 0;
  border-bottom: 1px solid #eee;
  padding-top: 5%;
}
.datepicker-month {
  font-family: "campton";
  font-size: 1.5rem;
  line-height: 2.5rem;
}
.datepicker-month strong {
  margin-left: 2%;
  font-size: 2.5rem;
  font-weight: bold;
}
.datepicker-calendar {
  text-align: center;
  table-layout: fixed;
}
.datepicker-calendar thead,
.datepicker-year {
  display: none;
}
.datepicker-calendar tbody td {
  padding: 0.344rem;
  font-size: 0;
  line-height: 0;
  pointer-events: none;
}
.datepicker-calendar tbody td span,
.datepicker-calendar tbody td a {
  display: block;
  margin: 0 auto;
  width: 2.8125rem;
  height: 2.8125rem;
  text-decoration: none;
  font-size: 1.1rem;
  font-family: "Helvetica Neue";
  line-height: 2.8125rem;
  color: #777;
  border: 1px solid transparent;
  border-radius: 50%;
}
.datepicker-calendar tbody td.datepicker-week-end:first-child span,
.datepicker-calendar tbody td.datepicker-week-end:first-child a {
  color: #ff6666;
}
.datepicker-calendar tbody td.datepicker-current-day span,
.datepicker-calendar tbody td.datepicker-current-day a {
  border-color: #000;
  background-color: #000;
  color: #fff !important;
}
.d-day {
  display: flex;
  justify-content: center;
  padding-top: 10%;
  padding-bottom: 10%;
}
.heart {
  color: #ff4e7f;
}
</style>
