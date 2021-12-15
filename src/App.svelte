<link rel="stylesheet" href="https://s3.amazonaws.com/data.minnpost/projects/minnpost-styles/0.0.6-alpha/minnpost-styles.min.css" type="text/css">
<link href="https://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet"> 


<style>

	.mp .todayis {
		text-align: center;
	}

	.mp .dayssince {
		text-align: center;
		font-size: 4em;
		color: #0D57A0;
		padding: 0.5em;
	}

	.mp .description {
		margin-bottom: 5em;
		font-size: 1em;
		text-align: center;
	}
</style>

<script>
	import { onMount } from "svelte";

	let today = 0;
	let formatted_date = ""
	let days = []
	let months = []

	onMount(async function() {
		const response = await fetch(`https://worldtimeapi.org/api/timezone/America/Chicago`);
		const json = await response.json();
		today = new Date(json.datetime);

		days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
		months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
		formatted_date = days[today.getDay()] + ", " + months[today.getMonth()] + " " + today.getDate() + ", " + today.getFullYear();
	});

	function calculateTimeDelta(today, date) {
		var plural = "s"
		var dayDelta = Math.floor((today - date) / (24 * 60 * 60 * 1000));
		if (dayDelta === 1) {plural = ""}
		return dayDelta  + " day" + plural;
	}



</script>

<div class="mp">

{#if today === 0}
	<div class="loading-container">
		<i class="loading"></i> Loading...
	</div> 
{:else}
<div class="todayis">
	<p class="xlarge">Today is {formatted_date}.</p>
</div>

<h1>How long has it been since…</h1>

<h4>…Minnesota surpassed 10,000 deaths from COVID-19: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2021-12-15T00:00:00.00000-05:00"))}</div>

<div class="description">On December 15, 2021, the Minnesota Department of Health announced that 54 more Minnesotans had died of COVID-19, <a href="https://minnesota.cbslocal.com/2021/12/15/covid-in-minnesota-us-surpasses-800k-deaths-mdh-reports-2231-new-cases/">bringing the total for the entire pandemic to 10,018.</a></div>


<h4>…Minnesota surpassed 5,000 deaths from COVID-19: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-12-24T00:00:00.00000-05:00"))}</div>

<div class="description">On December 24, 2020 — Christmas Eve — the Minnesota Department of Health announced that 79 more Minnesotans had died of COVID-19, <a href="https://www.minnpost.com/health/2020/12/the-daily-coronavirus-update-79-deaths-bring-total-to-more-than-5000-in-minnesota/">bringing the total for the entire pandemic to 5,050.</a></div>


<h4>…the number of confirmed COVID-19 cases in Minnesota passed 100,000: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-10-01T00:00:00.00000-05:00"))}</div>

<div class="description">On October 1, 2020, <a href="https://www.minnpost.com/health/2020/10/the-daily-coronavirus-update-minnesota-surpasses-100000-total-covid-19-cases/">the Minnesota Department of Health said there had been a total of 100,200 confirmed cases of COVID-19</a> in Minnesota since the start of the pandemic.</div>


<h4>…the number of deaths from COVID-19 in Minnesota passed 2,000: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-09-26T00:00:00.00000-05:00"))}</div>

<div class="description">On September 26, 2020, the Minnesota Department of Health <a href="https://www.minnpost.com/health/2020/09/the-daily-coronavirus-update-4-more-deaths-1075-new-cases-in-minnesota/">announced that a total of 2,004 Minnesotans had died of COVID-19 over the course of the pandemic.</a></div>


<h4>…the number of deaths from COVID-19 in Minnesota passed 1,000: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-05-30T00:00:00.00000-05:00"))}</div>

<div class="description">On May 30, 2020, the Minnesota Department of Health <a href="https://www.minnpost.com/health/2020/05/the-daily-coronavirus-update-30-more-die-of-covid-19-as-minnesotas-death-toll-tops-1000/">announced that a total of 1,026 Minnesotans had died of COVID-19 over the course of the pandemic.</a></div>


<h4>…the number of confirmed COVID-19 cases in Minnesota passed 10,000: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-05-08T00:00:00.00000-05:00"))}</div>

<div class="description">On May 8, 2020, the Minnesota Department of Health <a href="https://www.minnpost.com/health/2020/05/the-daily-coronavirus-update-minnesota-surpasses-10000-confirmed-cases-state-bans-large-in-person-graduation-ceremonies/">announced there were a total of 10,088 confirmed cases of COVID-19 in Minnesota.</a></div>


<h4>…the number of confirmed COVID-19 cases in Minnesota passed 1,000: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-04-07T00:00:00.00000-05:00"))}</div>

<div class="description">The total number of confirmed COVID-19 cases on <a href="https://www.minnpost.com/health/2020/04/the-daily-coronavirus-update-minnesota-surpasses-1000-confirmed-cases-walz-expected-to-extend-stay-at-home-order/">April 7, 2020 was 1,069</a>. Note that, due to lack of testing capabilities, the actual number of cases in the state is assumed to be much higher.</div>

<h4>…Minnesota’s tenth death from COVID-19: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-03-30T00:00:00.00000-05:00"))}</div>

<div class="description">The Minnesota Department of Health announced the <a href="https://www.minnpost.com/health/2020/03/the-daily-coronavirus-update-10th-minnesota-death-reported-state-clarifies-who-are-essential-workers/">tenth death from the disease in Minnesota on March 30, 2020.</a></div>

<h4>…Gov. Tim Walz’s stay-at-home order went into effect: </h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-03-27T00:00:00.00000-05:00"))}</div>

<div class="description">Gov. Tim Walz’s order <a href="https://www.minnpost.com/state-government/2020/03/walz-issues-stay-at-home-order-for-minnesota-extends-closure-of-schools-bars-and-restaurants/">went into effect on Friday, March 27 at 11:59 p.m.</a></div>

<h4>…the first Minnesotan died from coronavirus:</h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-03-19T00:00:00.00000-05:00"))}</div>

<div class="description">A Ramsey County resident in her 80s <a href="https://www.minnpost.com/health/2020/03/the-daily-coronavirus-update-minnesota-sees-first-death-from-covid-19/">died from COVID-19 on Thursday, March 19.</a></div>

<h4>…Minnesota bars and restaurants were ordered closed:</h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-03-17T00:00:00.00000-05:00"))}</div>

<div class="description">Gov. Tim Walz ordered Minnesota <a href="https://www.minnpost.com/state-government/2020/03/walz-orders-bars-and-restaurants-closed-as-part-of-latest-effort-to-slow-spread-of-covid-19/">bars and restaurants to close on Tuesday, March 17 at 5 p.m.</a></div>

<h4>…Gov. Tim Walz declared a state of peacetime emergency in Minnesota:</h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-03-13T00:00:00.00000-05:00"))}</div>

<div class="description">Gov. Tim Walz <a href="https://www.minnpost.com/state-government/2020/03/walz-declares-state-of-emergency-for-minnesota-urges-canceling-or-postponing-all-large-events/">declared a state of peacetime emergency on March 13.</a> The declaration gave the governor increased powers to act quickly to respond to the pandemic.</div>


<h4>…WHO delcared COVID-19 a pandemic:</h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-03-11T00:00:00.00000-05:00"))}</div>

<div class="description">The World Health Organization <a href="https://time.com/5791661/who-coronavirus-pandemic-declaration/">declared COVID-19 a pandemic on March 11, after cases were confirmed in 110 countries and territories.</a></div>

<h4>…Minnesota’s first confirmed COVID-19 case:</h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-03-06T00:00:00.00000-05:00"))}</div>

<div class="description">The Minnesota Department of Health <a href="https://www.health.state.mn.us/news/pressrel/2020/covid19030620.html">announced Minnesota’s first confirmed case of COVID-19 on March 6.</a></div>

<h4>…the first confirmed case of COVID-19 in U.S.:</h4>

<div class="dayssince">{calculateTimeDelta(today, new Date("2020-01-22T00:00:00.00000-05:00"))}</div>

<div class="description">The CDC confirmed the <a href="https://www.smithsonianmag.com/smart-news/wuhan-coronavirus-180974027/">U.S.’s first case of COVID-19, a man in Washington, on&nbsp;January&nbsp;22</a>.</div>

{/if}

</div>
