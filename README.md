# Next.js

By using the Next.js framework, optimizations you traditionally manually code in native HTML get written for you by the Next.js framework. So use the framework components instead of native HTML whenvever possible. Below are the most common Next.js components.
## next/font
Next.js downloads font files at build time and hosts them with your other static assets.

### Example
Import the font and limit font data by subset.
```tsx
import { Lusitana } from 'next/font/google';
const lusitana = Lusitana({
  weight: ['400', '700'],
  subsets: ['latin'],
});
```
Then apply the font via classname.
```tsx
<body className={`${lusitana.className}`}>
  <h1>This will pick up font-weight of 700</h1>
  <p>This will pick up font-weight of 400</p>
</body>
```

### Output
Next.js automatically pre-renders font syntax to ensure **peak Lighthouse scores**, handling the manual optimization details for you.

## next/image
```tsx
import Image from 'next/image';
```
Images are hosted in the /public folder.
```tsx
<Image
  src="/hero-desktop.png"
  width={1000}
  height={760}
  alt="Screenshots of the dashboard project showing desktop version"
/>
```
The width and height attributes specify the ***intrinsic*** dimensions of the image, which are used to calculate the aspect ratio, not the actual rendered size.

### Output
Next.js automates image optimization.

- **Generates Markup**: Generates srcset and/or picture tags automatically; no manual coding required.
- **Built-in Optimization**: Handles resizing and compression for you.

## file-system routing
Next.js uses file-system routing where folders are used to create nested routes. Each folder represents a route segment that maps to a URL segment.

![file-system routing](/folders-to-url-segments.avif)

### page.tsx

***page.tsx*** is required for the route to be accessed as a webpage:

![dashboard route](/dashboard-route.avif)

Here's of an example of many ***page.tsx*** files mapped to urls based off of file-system routing by simply creating a page.tsx React component under each folder:

![many pages and its routes](/routing-solution.avif)


A page.tsx React component at its bare minimum can look like:
```tsx
export default function Page() {
  return <p>Hello World!</p>;
}
```

### layout.tsx
![layout.tsx](/shared-layout.avif)
When a layout.tsx file is present, the content rendered by page.tsx is passed as the children prop to the layout.tsx component.

This layout.tsx file is used as the parent component for its nested routes such as the page.tsx file in subdirectories customers and invoices.

## partial rendering
![partial rendering](/partial-rendering-dashboard.avif)
One benefit of using layouts in Next.js is that on navigation, only the page components update while the layout won't re-render. 

## colocation
In Next.js, “colocation” means keeping all route-related files (components, styles, logic) in the same folder as the route’s main file.