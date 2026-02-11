# Next.js

## next/font
```tsx
import { Lusitana } from 'next/font/google';
const lusitana = Lusitana({
  weight: ['400', '700'],
  subsets: ['latin'],
});
```

```tsx
<body className={`${lusitana.className}`}>
  <h1>This will pick up font-weight of 700</h1>
  <p>This will pick up font-weight of 400</p>
</body>
```

## next/image
```tsx
import Image from 'next/image';
```

```tsx
<Image
  src="/hero-desktop.png"
  width={1000} /* intrinsic dimensions required */
  height={760}
  alt="Screenshots of the dashboard project showing desktop version"
/>
```

## next/link
```tsx
import Link from 'next/link';
```
```tsx
<Link href="/dashboard">Dashboard</Link>
```

## next/script
```tsx
import Script from 'next/script'
```
```tsx
<Script src="/script.js" />
```

## file-system routing
Root Segment > Segment > Leaf Segment

![segments](/segments.png)

### page.tsx
**default export a React component**:
```tsx
export default function Page() {
  return <p>Hello World!</p>;
}
```

### layout.tsx
![layout.tsx](/shared-layout.avif)
When a layout.tsx file is present, the content rendered by page.tsx is passed as the children prop to the layout.tsx component.

This layout.tsx file is used as the parent component for its nested routes such as the page.tsx file in subdirectories (customers and invoices).

### partial rendering
During navigation, only the page components update. The layout does not re-render.

### colocation
In Next.js, “colocation” means keeping all route-related files (components, styles, logic) in the same folder as the route’s main file.