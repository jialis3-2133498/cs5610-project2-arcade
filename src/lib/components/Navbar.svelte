<script>
    import { page } from '$app/state';
</script>

<header>
    <nav aria-label="Main navigation">
        <p class="site-title">Jiali Sheng's Arcade</p>
        <ul>
            <li>
                <a href="/" aria-current={page.url.pathname === '/' ? 'page' : undefined}>
                    Home
                </a>
            </li>
            <li>
                <a href="/crossword" aria-current={page.url.pathname === '/crossword' ? 'page' : undefined}>
                    Crossword
                </a>
            </li>
            <li>
                <a href="/about" aria-current={page.url.pathname === '/about' ? 'page' : undefined}>
                    About
                </a>
            </li>
            <li>
                <a href="/contact" aria-current={page.url.pathname === '/contact' ? 'page' : undefined}>
                    Contact
                </a>
            </li>
            <li>
                <a href="/2048" aria-current={page.url.pathname === '/2048' ? 'page' : undefined}>
                    2048
                </a>
            </li>
        </ul>
    </nav>
</header>