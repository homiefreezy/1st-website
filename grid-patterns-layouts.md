# CSS Grid Patterns & Real-World Website Layouts
## Practical Examples for Modern Websites

### 1. Holy Grail Layout
The classic website layout with header, footer, main content, and sidebars.

```html
<div class="holy-grail">
    <header>Header</header>
    <nav class="left-sidebar">Left Sidebar</nav>
    <main>Main Content</main>
    <aside class="right-sidebar">Right Sidebar</aside>
    <footer>Footer</footer>
</div>
```

```css
.holy-grail {
    display: grid;
    grid-template-areas:
        "header  header  header"
        "left    main    right"
        "footer  footer  footer";
    grid-template-columns: 200px 1fr 200px;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
    gap: 20px;
}

header { grid-area: header; }
.left-sidebar { grid-area: left; }
main { grid-area: main; }
.right-sidebar { grid-area: right; }
footer { grid-area: footer; }

/* Responsive */
@media (max-width: 768px) {
    .holy-grail {
        grid-template-areas:
            "header"
            "main"
            "left"
            "right"
            "footer";
        grid-template-columns: 1fr;
    }
}
```

### 2. Magazine Layout
Perfect for content-rich websites with featured articles.

```html
<div class="magazine-layout">
    <article class="featured">Featured Article</article>
    <article class="standard">Article 1</article>
    <article class="standard">Article 2</article>
    <article class="horizontal">Wide Article</article>
    <article class="standard">Article 3</article>
    <article class="standard">Article 4</article>
</div>
```

```css
.magazine-layout {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    padding: 20px;
}

.featured {
    grid-column: span 2;
    grid-row: span 2;
    background: #f0f0f0;
    min-height: 400px;
}

.standard {
    grid-column: span 1;
    min-height: 200px;
    background: #e0e0e0;
}

.horizontal {
    grid-column: span 2;
    background: #d0d0d0;
    min-height: 200px;
}

@media (max-width: 768px) {
    .magazine-layout {
        grid-template-columns: repeat(2, 1fr);
    }
    
    .featured,
    .horizontal {
        grid-column: span 2;
    }
}
```

### 3. Portfolio Grid
Ideal for showcasing work with different sized items.

```html
<div class="portfolio-grid">
    <div class="portfolio-item wide">Wide Project</div>
    <div class="portfolio-item">Normal Project</div>
    <div class="portfolio-item tall">Tall Project</div>
    <div class="portfolio-item">Normal Project</div>
    <div class="portfolio-item wide tall">Featured Project</div>
    <div class="portfolio-item">Normal Project</div>
</div>
```

```css
.portfolio-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    padding: 20px;
}

.portfolio-item {
    background: #eee;
    min-height: 200px;
    border-radius: 8px;
}

.wide { grid-column: span 2; }
.tall { grid-row: span 2; }

@media (max-width: 768px) {
    .portfolio-grid {
        grid-template-columns: 1fr;
    }
    
    .wide, .tall {
        grid-column: auto;
        grid-row: auto;
    }
}
```

### 4. E-commerce Product Grid
Common pattern for product listings with featured items.

```html
<div class="product-grid">
    <div class="product-filters">Filters</div>
    <div class="products">
        <div class="product">Product 1</div>
        <div class="product">Product 2</div>
        <div class="product featured">Featured Product</div>
        <div class="product">Product 3</div>
        <div class="product">Product 4</div>
    </div>
</div>
```

```css
.product-grid {
    display: grid;
    grid-template-columns: 250px 1fr;
    gap: 30px;
    padding: 20px;
}

.products {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 20px;
}

.product {
    background: white;
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
}

.featured {
    grid-column: span 2;
    grid-row: span 2;
}

@media (max-width: 768px) {
    .product-grid {
        grid-template-columns: 1fr;
    }
    
    .featured {
        grid-column: span 1;
        grid-row: span 1;
    }
}
```

### 5. Blog Layout
Modern blog layout with featured posts and sidebar.

```html
<div class="blog-layout">
    <header class="blog-header">Blog Title</header>
    <main class="blog-main">
        <article class="featured-post">Featured Post</article>
        <article class="post">Regular Post</article>
        <article class="post">Regular Post</article>
        <article class="post">Regular Post</article>
    </main>
    <aside class="blog-sidebar">
        <div class="widget">About</div>
        <div class="widget">Categories</div>
        <div class="widget">Recent Posts</div>
    </aside>
</div>
```

```css
.blog-layout {
    display: grid;
    grid-template-areas:
        "header header"
        "main   sidebar";
    grid-template-columns: 1fr 300px;
    gap: 30px;
    padding: 20px;
    max-width: 1200px;
    margin: 0 auto;
}

.blog-header {
    grid-area: header;
}

.blog-main {
    grid-area: main;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
}

.featured-post {
    grid-column: 1 / -1;
    min-height: 300px;
    background: #f5f5f5;
}

.blog-sidebar {
    grid-area: sidebar;
}

.widget {
    margin-bottom: 20px;
    padding: 15px;
    background: #f5f5f5;
}

@media (max-width: 768px) {
    .blog-layout {
        grid-template-areas:
            "header"
            "main"
            "sidebar";
        grid-template-columns: 1fr;
    }
    
    .blog-main {
        grid-template-columns: 1fr;
    }
}
```

### 6. Dashboard Layout
Common pattern for admin panels and dashboards.

```html
<div class="dashboard">
    <header class="dash-header">Dashboard Header</header>
    <nav class="dash-nav">Navigation</nav>
    <main class="dash-main">
        <div class="card">Stats</div>
        <div class="card">Graph</div>
        <div class="card wide">Timeline</div>
        <div class="card">Tasks</div>
        <div class="card">Messages</div>
    </main>
</div>
```

```css
.dashboard {
    display: grid;
    grid-template-areas:
        "nav header"
        "nav main";
    grid-template-columns: 220px 1fr;
    grid-template-rows: 60px 1fr;
    min-height: 100vh;
}

.dash-header {
    grid-area: header;
    background: #fff;
    border-bottom: 1px solid #ddd;
}

.dash-nav {
    grid-area: nav;
    background: #1a1a1a;
    color: white;
}

.dash-main {
    grid-area: main;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    padding: 20px;
    background: #f0f2f5;
}

.card {
    background: white;
    border-radius: 8px;
    padding: 20px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.wide {
    grid-column: 1 / -1;
}

@media (max-width: 768px) {
    .dashboard {
        grid-template-areas:
            "header"
            "nav"
            "main";
        grid-template-columns: 1fr;
        grid-template-rows: 60px auto 1fr;
    }
}
```