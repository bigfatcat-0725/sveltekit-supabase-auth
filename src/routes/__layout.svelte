<script>
	import { session } from '$app/stores';
	import supabase from '$lib/db';
	import { browser } from '$app/env';
	import { goto } from '$app/navigation';

	// Whether the app is running in the browser or on the server.
	if (browser) {
		$session = supabase.auth.session();
		setTimeout(() => ($session ? goto('/') : goto('/signup')));
		// auth가 체인지 될때 (로그인 <-> 로그아웃)
		supabase.auth.onAuthStateChange((event, sesh) => {
			$session = sesh;
			setTimeout(() => ($session ? goto('/') : goto('/signup')));
		});
	}
</script>

<div>
	<slot />
	<pre>
    {JSON.stringify($session, null, 2)}
  </pre>
</div>
