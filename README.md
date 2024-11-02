# farm-fe-conf
Farm Fe configuration files

## Common React and SolidJS

```bash
bun -D tailwindcss postcss autoprefixer
bun tailwindcss init -p
```
### Modify `tailwind.config.js`

```typescript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### Add `postcss` processing

```bash
bun add -D @farmfe/js-plugin-postcss
```

### Add `index.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## React - TailwindCSS - `farm.config.ts`

```typescript
import { defineConfig } from '@farmfe/core';
import farmPostcssPlugin from '@farmfe/js-plugin-postcss'

export default defineConfig({
  plugins: ['@farmfe/plugin-react', farmPostcssPlugin()]
});
```

## SolidJS - TailwindCSS - `farm.config.ts`

```typescript
// import { defineConfig } from '@farmfe/core';
// import solid from 'vite-plugin-solid';

// export default defineConfig({
//   vitePlugins: [
//     () => ({
//       vitePlugin: solid(),
//       filters: ['\\.tsx$', '\\.jsx$']
//     })
//   ]
// });

import { defineConfig } from '@farmfe/core';
import farmJsPluginSolid from '@farmfe/js-plugin-solid'
import farmPostcssPlugin from '@farmfe/js-plugin-postcss'

export default defineConfig({  
  plugins: [farmJsPluginSolid(), farmPostcssPlugin()]
});
```
