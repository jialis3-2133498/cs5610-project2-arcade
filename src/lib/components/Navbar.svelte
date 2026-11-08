<script>
	import { page } from '$app/state';
	import { resolve } from '$app/paths';
</script>

<header>
	<nav aria-label="Main navigation">
		<p class="site-title">Jiali Sheng's Arcade</p>
		<ul>
			<li>
				<a href={resolve('/')} aria-current={page.route.id === '/' ? 'page' : undefined}> Home </a>
			</li>
			<li>
				<a
					href={resolve('/crossword')}
					aria-current={page.route.id === '/crossword' ? 'page' : undefined}
				>
					Crossword
				</a>
			</li>
			<li>
				<a href={resolve('/about')} aria-current={page.route.id === '/about' ? 'page' : undefined}>
					About
				</a>
			</li>
			<li>
				<a
					href={resolve('/contact')}
					aria-current={page.route.id === '/contact' ? 'page' : undefined}
				>
					Contact
				</a>
			</li>
			<li>
				<a href={resolve('/2048')} aria-current={page.route.id === '/2048' ? 'page' : undefined}>
					2048
				</a>
			</li>
		</ul>
	</nav>
</header>
