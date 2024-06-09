<script lang="ts">
	import Footer from '$lib/components/Footer.svelte';
	import Main from '$lib/components/Main.svelte';
	import {
		Content,
		Header,
		HeaderNav,
		HeaderNavItem,
		SideNav,
		SideNavItems,
		SideNavLink,
		SkipToContent
	} from 'carbon-components-svelte';
	import 'carbon-components-svelte/css/g10.css';
	import { onMount } from 'svelte';

	let isSideNavOpen = false;
	let menus = [
		{
			text: 'About',
			href: '/about'
		},
		{
			text: 'Saju Reading',
			href: '/saju'
		},
		{
			text: 'FAQs',
			href: '/faq'
		},
		{
			text: 'Contact',
			href: '/contact'
		}
	];

	onMount(() => {});
</script>

<Header platformName="Saju Insights" href="/" expandedByDefault={false} bind:isSideNavOpen>
	<svelte:fragment slot="skip-to-content">
		<SkipToContent />
	</svelte:fragment>
	<HeaderNav>
		{#each menus as menu}
			<HeaderNavItem href={menu.href} text={menu.text} />
		{/each}
	</HeaderNav>
</Header>

<SideNav bind:isOpen={isSideNavOpen}>
	<SideNavItems>
		{#each menus as menu}
			<SideNavLink href={menu.href} text={menu.text} />
		{/each}
	</SideNavItems>
</SideNav>

<Content>
	<Main>
		<slot></slot>
	</Main>
</Content>

<Footer></Footer>
