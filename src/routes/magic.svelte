<script>
	import supabase from '$lib/db';

	let email, password;

	const signUp = async () => {
		const { user, session, error } = await supabase.auth.signIn({
			email,
			password
		});
		if (error) alert(error.message);
	};
</script>

<form on:submit|preventDefault={signUp}>
	<label for="email">Email</label>
	<input bind:value={email} id="email" type="email" />
	<button>MAGIC</button>
</form>
<a href="/signin">Need an account?</a>
<a href="/magic">Want a magic link?</a>
