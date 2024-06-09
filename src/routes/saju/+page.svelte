<script lang="ts">
	let name = '';
	let gender = '';
	let birthDate = '';
	let birthTime = '';
	let birthPlace = '';
</script>

<h1>Start Your Saju Reading</h1>

<form>
	<label for="name">Name:</label>
	<input type="text" id="name" bind:value={name} required />

	<label for="gender">Gender:</label>
	<select id="gender" bind:value={gender} required>
		<option value="" disabled selected>Select your gender</option>
		<option value="male">Male</option>
		<option value="female">Female</option>
		<option value="other">Other</option>
	</select>

	<label for="birthDate">Date of Birth:</label>
	<input type="date" id="birthDate" bind:value={birthDate} required />

	<label for="birthTime">Time of Birth:</label>
	<input type="time" id="birthTime" bind:value={birthTime} required />

	<label for="birthPlace">Place of Birth:</label>
	<input type="text" id="birthPlace" bind:value={birthPlace} required />

	<button type="submit">Get Your Saju Reading</button>
</form>
