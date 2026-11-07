<script>
    import '../app.css';
    import favicon from '#lib/assets/favicon.svg';
    import Navbar from '../lib/components/Navbar.svelte';
    import { page } from '$app/state';

    /** @type {{ children: import('svelte').Snippet }} */
    let { children } = $props();
</script>

<svelte:head>
    <link rel="icon" href={favicon} />
</svelte:head>

<Navbar />

<main class:crossword-layout={page.url.pathname === '/crossword'}>
    {@render children()}
</main>

<footer class="site-footer">
    <p>© 2026 Jiali Sheng. Built with HTML, CSS, JavaScript, and SvelteKit.</p>
</footer>