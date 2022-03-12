<script>
	import supabase from '$lib/db';

	const signUp = async () => {
		await supabase.auth.signUp({
			email: 'example@email.com',
			password: 'example-password'
		});
	};

	let room = '';
	const addRoom = async () => {
		const newRoom = await supabase.from('rooms').insert({ name: room, size: 'big' });
	};

	const getRooms = () => {
		return supabase.from('rooms').select(`*`);
	};

	const signOut = async () => {
		const { error } = await supabase.auth.signOut();
		if (error) alert(error.message);
	};
</script>

<!-- {#await getRooms()}
	Loading..
{:then response}
	<pre>{JSON.stringify(response, null, 2)}</pre>
{/await} -->
<input bind:value={room} />
<button on:click={addRoom}>Add Room</button>
<button on:click={signUp}>Sign Up</button>
<button on:click={signOut}>Sign Out</button>

<a href="/signin"><h1>여기로 가세요</h1></a>
