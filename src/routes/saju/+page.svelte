<script lang="ts">
	import { goto } from '$app/navigation';
	import Gap from '$lib/components/Gap.svelte';
	import Meta from '$lib/components/Meta.svelte';
	import { db } from '$lib/firebase';
	import {
		Button,
		DatePicker,
		DatePickerInput,
		Form,
		Select,
		SelectItem,
		TextInput,
		TimePicker,
		TimePickerSelect
	} from 'carbon-components-svelte';
	import { addDoc, collection, serverTimestamp } from 'firebase/firestore';

	let name = '';
	let email = '';
	let gender = 'Male';
	let birthDate = '';
	let birthTime = '';
	let birthTimePeriod = 'pm';
	let birthPlace = '';

	async function submitSaju() {
		if (!validate()) {
			return;
		}

		try {
			const docRef = await addDoc(collection(db, 'saju-requests'), {
				name,
				email,
				gender,
				birthDate,
				birthTime,
				birthTimePeriod,
				birthPlace,
				timestamp: serverTimestamp()
			});

			alert('Your Saju reading is on its way! Please check your email for more details.');
		} catch (e) {
			console.error('Error adding document: ', e);
			alert('An error occurred while processing your request. Please try again later.');
		} finally {
			goto('/');
		}
	}

	function validate() {
		if (!name || !email || !birthDate || !birthTime || !birthPlace) {
			alert('Please fill in all required fields.');
			return false;
		}

		return true;
	}

	function handleGender(event: any) {
		gender = event.target.value;
	}

	function handleDate(event: any) {
		birthDate = event.detail.dateStr;
	}

	function handleTime(event: any) {
		birthTime = event.target.value;
	}
</script>

<Meta title="Saju Reading"></Meta>

<h1>Start Your Saju Reading</h1>
<Gap></Gap>

<Form on:submit={submitSaju}>
	<TextInput labelText="Name" placeholder="Enter your name" bind:value={name} required></TextInput>
	<Gap></Gap>

	<TextInput
		type="email"
		labelText="Email"
		placeholder="Enter your email"
		bind:value={email}
		required
	></TextInput>
	<Gap></Gap>

	<Select labelText="Gender" on:change={handleGender}>
		<SelectItem value="Male"></SelectItem>
		<SelectItem value="Female"></SelectItem>
		<SelectItem value="Other"></SelectItem>
	</Select>

	<Gap></Gap>

	<DatePicker datePickerType="single" on:change={handleDate}>
		<DatePickerInput labelText="Date of Birth" placeholder="mm/dd/yyyy" />
	</DatePicker>
	<Gap></Gap>

	<TimePicker labelText="Time of Birth" placeholder="hh:mm" on:change={handleTime}>
		<TimePickerSelect bind:value={birthTimePeriod}>
			<SelectItem value="am" text="AM" />
			<SelectItem value="pm" text="PM" />
		</TimePickerSelect>
	</TimePicker>
	<Gap></Gap>

	<TextInput
		labelText="Place of Birth"
		placeholder="Seoul, South Korea"
		bind:value={birthPlace}
		required
	></TextInput>
	<Gap></Gap>

	<Button type="submit">Get Your Saju Reading</Button>
</Form>
