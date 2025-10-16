<script lang="ts">
	let decodedSavefile: Array<any> = [];
	let encodedSavefile: string = "";
	let readSavefileError: boolean = true;

	function reverseString(str: string): string {
		return str.split("").reverse().join("");
	}

	function handleSavefileInput(event: Event) {
		const textarea = event.target as HTMLTextAreaElement;
		const savefileContent = textarea.value;
		try {
			let decoded = atob(reverseString(savefileContent));
			let partiallyDecodedSavefile: Array<string> = JSON.parse(JSON.parse(decoded));

			for (let i = 0; i < partiallyDecodedSavefile.length; ++i) {
				partiallyDecodedSavefile[i] = JSON.parse(atob(reverseString(partiallyDecodedSavefile[i])));
			}
			decodedSavefile = partiallyDecodedSavefile;

			[
				"get2763intennis",
				"winagameoftennis",
				"get2763gtttatint",
				"slapTD2763",
				"get2763",
				"lemons",
				"get10perfectsCAKEWALK",
				"2763lemons",
				"perfectfacematch",
				"10energydrinks",
				"5minuteGTTTATINT",
				"tauntLogo",
				"oddDroplets40",
				"750altitudeCAKEWALK",
				"get15000gtttatint",
				"1000altitudeCAKEWALK",
				"blockplatformgtttatint",
				"aprilFools_boom",
				"brew"
			].forEach((achName) => {
				if (!(achName in decodedSavefile[16])) decodedSavefile[16][achName] = false;
			});

			encodeSavefile();
			readSavefileError = false;
		} catch (error) {
			readSavefileError = true;
		}
	}

	async function encodeSavefile() {
		await new Promise((r) => setTimeout(r, 10));
		let partiallyEncodedSavefile: Array<string> = [];
		for (let i = 0; i < decodedSavefile.length; ++i) {
			console.log(decodedSavefile[i]);
			partiallyEncodedSavefile.push(reverseString(btoa(JSON.stringify(decodedSavefile[i]))));
		}
		encodedSavefile = reverseString(btoa(JSON.stringify(JSON.stringify(partiallyEncodedSavefile))));
	}
</script>

<h1>myTeardrop Savefile Editor</h1>
<h2>by <a href="https://github.com/Noxturnix" target="_blank">@Noxturnix</a></h2>
<p style="color: gray">To get your savefile, go to Settings > Backup > Advanced > Copy Backup.</p>
<textarea
	name="savefile"
	id="savefile"
	placeholder="Paste your myTeardrop savefile here."
	on:input={handleSavefileInput}
></textarea>
{#if !readSavefileError}
	<div id="savefile-editor">
		<div>
			<span><b>Coins:&nbsp;</b></span><input
				type="number"
				name="coins"
				bind:value={decodedSavefile[0]}
				on:input={encodeSavefile}
			/><br />
		</div>
		<div>
			<span><b>Level:&nbsp;</b></span><input
				type="number"
				name="level"
				bind:value={decodedSavefile[15]}
				on:input={encodeSavefile}
			/><br />
		</div>
		<div>
			<span><b>Achivements:&nbsp;</b></span><br />
			{#each Object.keys(decodedSavefile[16]) as key}
				<span>{key}:&nbsp;</span><input
					type="checkbox"
					name={key}
					bind:checked={decodedSavefile[16][key]}
					on:input={encodeSavefile}
				/><br />
			{/each}
		</div>
		<div>
			<span><b>Edited savefile:</b></span><br />
			<textarea name="esavefile" id="esavefile" bind:value={encodedSavefile} readonly></textarea>
			<p style="color: gray">Reload the game webpage and try uploading again if it doesn't work.</p>
		</div>
	</div>
{:else}
	<p style="color: red;">Error reading savefile.</p>
{/if}

<style>
	#savefile {
		width: 22em;
		height: 8em;
		box-sizing: border-box;
		font-family: monospace;
		font-size: 1em;
		padding: 1em;
		resize: none;
	}

	#esavefile {
		width: 22em;
		height: 8em;
		box-sizing: border-box;
		font-family: monospace;
		font-size: 1em;
		padding: 1em;
		resize: none;
	}

	#savefile-editor {
		margin-top: 1em;
	}

	#savefile-editor div {
		margin-top: 0.4em;
	}
</style>
