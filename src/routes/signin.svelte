<script>
	import supabase from '$lib/db';

	let email, password;

	const signUp = async () => {
		const { user, session, error } = await supabase.auth.signIn({
			email,
			password
		});
		console.log(session);
		if (error) alert(error.message);
	};
</script>

<form on:submit|preventDefault={signUp}>
	<label for="email">Email</label>
	<input bind:value={email} id="email" type="email" />
	<label for="password">Password</label>
	<input bind:value={password} id="password" type="password" />
	<button>Sign In</button>
</form>

<a href="/signup">Need an account?</a>
<a href="/magic">Want a magic link?</a>
