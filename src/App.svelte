<script>
	import RecordSet from './components/shared/RecordSet.svelte'
	const fields = {
		'login.username': true,
		'name.last': true,
		'name.first': true,
		'email': true
	};

	let records = [];
	let isLoading = false;

	const load = () => {
		isLoading = true;
		fetch('https://randomuser.me/api/?results=25')
			.then(response => response.json())
			.then(data => {
				records = data.results;
				isLoading = false;
			})
	}

	load();
</script>

<p>
	Here are some users. I hope you like them.
	<button disabled={isLoading} on:click={load}>More</button>
</p>

<RecordSet fields={fields} records={records} />
