# Next.js
## Components

```tsx
import Image from 'next/image';
import Link from 'next/link';
import Form from 'next/form';
import Script from 'next/script';
```

### next/font

```tsx
import { Lusitana } from 'next/font/google';
const lusitana = Lusitana({
  weight: ['400', '700'],
});
```

```tsx
<body className={`${lusitana.className}`}>
```

## App Router: file-system based router
Root Segment > Segment > Leaf Segment

![segments](/segments.png)

### conventions

For all files, **default export a React component** and match the component name with the file.
> page.tsx

```tsx
export default function Page() {
  return <p>Hello World I'm a webpage!</p>;
}
```

A summary of the most common files used in App Router:
- page.tsx
- layout.tsx
- loading.tsx
- not-found.tsx
- error.tsx

> More listed at https://nextjs.org/docs/app/api-reference/file-conventions

#### layout.tsx
![layout.tsx](/shared-layout.avif)

For the root layout, name the component **RootLayout**

```tsx
export default function RootLayout({children}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  )
}
```

### colocation
In Next.js, “colocation” means keeping all route-related files (components, styles, logic) in the same folder as the route’s main file.