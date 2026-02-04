# Next.js

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