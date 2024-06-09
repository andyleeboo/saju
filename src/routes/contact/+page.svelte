<script lang="ts">
	import Gap from '$lib/components/Gap.svelte';
	import Meta from '$lib/components/Meta.svelte';
	import { db } from '$lib/firebase';
	import { Button, ButtonSet, Form, TextArea, TextInput } from 'carbon-components-svelte';
	import { addDoc, collection, serverTimestamp } from 'firebase/firestore';

	let name = '';
	let email = '';
	let message = '';

	async function submitInquiry() {
		try {
			const docRef = await addDoc(collection(db, 'inquiries'), {
				name,
				email,
				message,
				timestamp: serverTimestamp()
			});

			alert('Your message has been sent! You will receive a response shortly.');
		} catch (e) {
			console.error('Error adding document: ', e);
			alert('An error occurred while processing your request. Please try again later.');
		} finally {
			reset();
		}
	}

	function reset() {
		name = '';
		email = '';
		message = '';
	}
</script>

<Meta title="Contact"></Meta>

<h1>Contact Us</h1>

<Gap></Gap>

<p>
	If you have any questions, feedback, or inquiries, please feel free to contact us using the form
	below or through our email address.
</p>
<Gap></Gap>

<Form on:submit={submitInquiry}>
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
	<TextArea labelText="Message" bind:value={message} required></TextArea>
	<Gap></Gap>
	<ButtonSet>
		<Button type="submit">Submit</Button>
	</ButtonSet>
</Form>

<Gap></Gap>
<p>You can also reach us at: <a href="mailto:andyleeboo9@icloud.com">andyleeboo9@icloud.com</a></p>
