<script lang="ts">
  function getTdClass(index: number, day: number): string {
    let classes = [];
    if (index === 0) classes.push('weekend');
    if (day === 7) classes.push('today', 'current-day', 'active', 'hover');
    return classes.join(' ');
  }
  
  function getDDay(): number {
    const targetDate = new Date(2024, 9-1, 7);  // 월은 0부터 시작하므로 9월은 9-1로 설정
    const currentDate = new Date();
    const timeDifference = targetDate.getTime() - currentDate.getTime();
    return Math.ceil(timeDifference / (1000 * 60 * 60 * 24));
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
    <div id="calendar" class="datepicker">
      <div class="header">
        <div class="title">
          <span class="month"><strong>9</strong>月</span>
        </div>
        <div class="day-time">
          <span class="day">토요일</span> <span class="time">pm 2:00</span>
        </div>
      </div>
      <table class="calendar">
        <thead>
          <tr>
            {#each daysOfWeek as day, index}
              <th class="{getTdClass(index, 0)}">
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
.day-time {
  position: absolute;
  padding-top: 4%;
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
.header {
  margin: 0 -1.25rem 0.938rem;
}
.title {
  padding: 0.625rem 1.563rem 0;
  border-bottom: 1px solid #eee;
  padding-top: 5%;
}
.month {
  font-family: "campton";
  font-size: 1.5rem;
  line-height: 2.5rem;
}
.month strong {
  margin-left: 2%;
  font-size: 2.5rem;
  font-weight: bold;
  letter-spacing: 0.2em;
}
.calendar {
  text-align: center;
  table-layout: fixed;
}
.calendar thead {
  display: none;
}
.calendar tbody td {
  padding: 0.344rem;
  font-size: 0;
  line-height: 0;
  pointer-events: none;
}
.calendar tbody td span {
  display: block;
  margin: 0 auto;
  width: 2.5rem;
  height: 2.5rem;
  text-decoration: none;
  font-size: 1rem;
  font-family: "Helvetica Neue";
  line-height: 2.5rem;
  color: #777;
  border: 1px solid transparent;
  border-radius: 50%;
}
tbody td.weekend span{
  color: #ff6666;
}
.current-day span {
  border-color: #000;
  background-color: #000;
  color: #fff !important;
}
.d-day {
  font-size: 0.94rem;
  display: flex;
  justify-content: center;
  padding: 10% 0;
}
.heart {
  color: #ff4e7f;
}
</style>
