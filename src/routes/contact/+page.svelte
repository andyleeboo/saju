<script lang="ts">
	import { db } from '$lib/firebase';
	import { addDoc, collection, serverTimestamp } from 'firebase/firestore';

	let name = '';
	let email = '';
	let message = '';

	const submitInquiry = async () => {
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
		}
	};
</script>

<h1>Contact Us</h1>

<p>
	If you have any questions, feedback, or inquiries, please feel free to contact us using the form
	below or through our email address.
</p>

<form on:submit|preventDefault={submitInquiry}>
	<label for="name">Name:</label>
	<input type="text" id="name" bind:value={name} required />

	<label for="email">Email:</label>
	<input type="email" id="email" bind:value={email} required />

	<label for="message">Message:</label>
	<textarea id="message" bind:value={message} required></textarea>

	<button type="submit">Submit</button>
</form>

<p>You can also reach us at: <a href="mailto:andyleeboo9@icloud.com">andyleeboo9@icloud.com</a></p>
