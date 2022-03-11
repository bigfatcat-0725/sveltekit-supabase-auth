<script>
	import supabase from '$lib/db';

	let email, password;

	const signUp = async () => {
		const {
			user,
			session: sesh,
			error
		} = await supabase.auth.signUp({
			email,
			password
		});
		if (error) alert(error.message);
	};
</script>

<form on:submit|preventDefault={signUp}>
	<label for="email">Email</label>
	<input bind:value={email} id="email" type="email" />
	<label for="password">Password</label>
	<input bind:value={password} id="password" type="password" />
	<button>Sign Up</button>
</form>
<a href="/signin">Already have an account?</a>
<a href="/magic">Want a magic link?</a>
