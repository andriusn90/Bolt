<script lang="ts">
	import { bolt } from '$lib/State/Bolt';
	import { GlobalState } from '$lib/State/GlobalState';

	const { config } = GlobalState;
</script>

{#if bolt.hasBoltPlugins}
	<div class="mx-auto p-2">
		<label for="enable_plugins">Enable Bolt plugin loader: </label>
		<input
			type="checkbox"
			name="enable_plugins"
			id="enable_plugins"
			bind:checked={$config.rs_plugin_loader}
			class="ml-2"
		/>
	</div>
{/if}
<div class="mx-auto p-2">
	<label for="use_custom_uri">Use custom config URI: </label>
	<input
		id="use_custom_uri"
		type="checkbox"
		bind:checked={$config.use_custom_rs_config_uri}
		class="ml-2"
	/>
</div>
<div class="p-2">
	<textarea
		class="rounded border-2 border-slate-300 bg-slate-100 text-slate-950 disabled:opacity-50 dark:border-slate-800 dark:bg-slate-900 dark:text-slate-50"
		disabled={!$config.use_custom_rs_config_uri}
		rows="4"
		placeholder={bolt.env.default_config_uri}
		bind:value={$config.rs_config_uri}
	/>
</div>
<div class="p-2">
	<label for="rs_custom_launch_command">Launch command:</label>
	<br />
	<textarea
		id="rs_custom_launch_command"
		class="resize-x rounded border-2 border-slate-300 bg-slate-100 text-slate-950 disabled:opacity-50 dark:border-slate-800 dark:bg-slate-900 dark:text-slate-50"
		rows="1"
		cols="35"
		placeholder={'%command%'}
		bind:value={$config.rs_launch_command}
	/>
</div>
<div class="p-2">
	<label for="import_sh_path">Path to <code>import.sh</code> (for RS3 injection):</label>
	<br />
	<input
		id="import_sh_path"
		type="text"
		class="w-full rounded border-2 border-slate-300 bg-slate-100 text-slate-950 disabled:opacity-50 dark:border-slate-800 dark:bg-slate-900 dark:text-slate-50"
		placeholder="/home/user/engine/import.sh"
		bind:value={$config.import_sh_path}
	/>
	<small class="text-xs text-slate-500">Leave blank to disable automatic injection. The app will try to auto-detect <code>import.sh</code> in /engine/ if not set.</small>
</div>
