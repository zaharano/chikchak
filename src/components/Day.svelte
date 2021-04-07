<script>
	import FullCalendar from 'svelte-fullcalendar';
	import timeGridPlugin from '@fullcalendar/timegrid';
	import interactionPlugin from '@fullcalendar/interaction';

	let options = {
		initialView: 'timeGridDay',
		plugins: [timeGridPlugin, interactionPlugin],
		droppable: true,
		allDaySlot: false,
		slotMinTime: '08:00:00',
		slotMaxTime: '21:00:00',
		nowIndicator: true,
		headerToolbar: false,
		dayHeaders: false,
		editable: true,
		height: 'auto',
		eventColor: 'rgba(95, 191, 249, 1)'
	};
</script>

<div class="day-container">
	<div class="day">
		<FullCalendar {options} />
	</div>
</div>

<style>
	.day-container {
		background-color: rgba(95, 191, 249, 1);
		border-radius: 3px;
		padding: 15px;
	}
	.day {
		background-color: white;
		border-radius: 15px;
		width: 100%;
		overflow: hidden;
	}
</style>
