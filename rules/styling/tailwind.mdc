---
description: Tailwind CSS best practices for utility-first styling and component patterns
globs: ["**/*.tsx", "**/*.jsx", "**/*.vue", "**/*.svelte", "**/*.astro", "**/*.css"]
alwaysApply: false
---

# Tailwind CSS Best Practices

## Overview

| Aspect | Recommendation |
|--------|----------------|
| Version | Tailwind CSS v4 (2025) |
| Config | tailwind.config.ts |
| Approach | Utility-first, extract components when repeated |

---

## Class Organization

### Recommended Order

```tsx
// Order: Layout → Spacing → Sizing → Typography → Colors → Effects → States
<div className="
  flex items-center justify-between     // Layout
  p-4 gap-4                             // Spacing
  w-full max-w-md                       // Sizing
  text-sm font-medium                   // Typography
  text-gray-900 bg-white                // Colors
  rounded-lg shadow-md                  // Effects
  hover:bg-gray-50 focus:ring-2         // States
"/>
```

### Group Related Utilities

```tsx
// ✅ Good - grouped logically
<button className="
  px-4 py-2 
  text-sm font-semibold text-white 
  bg-blue-600 rounded-lg 
  hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500
">
  Click me
</button>

// ❌ Bad - random order
<button className="bg-blue-600 text-sm px-4 rounded-lg py-2 font-semibold hover:bg-blue-700 text-white focus:ring-2">
  Click me
</button>
```

---

## Responsive Design

### Mobile-First Approach

```tsx
// Start with mobile, add breakpoints for larger screens
<div className="
  grid grid-cols-1        // Mobile: 1 column
  md:grid-cols-2          // Tablet: 2 columns
  lg:grid-cols-3          // Desktop: 3 columns
  xl:grid-cols-4          // Large desktop: 4 columns
  gap-4
">
  {items.map(item => <Card key={item.id} />)}
</div>
```

### Breakpoint Reference

| Breakpoint | Min-width | Use case |
|------------|-----------|----------|
| `sm:` | 640px | Large phones |
| `md:` | 768px | Tablets |
| `lg:` | 1024px | Laptops |
| `xl:` | 1280px | Desktops |
| `2xl:` | 1536px | Large screens |

---

## Component Patterns

### Button Variants

```tsx
// Base button styles
const buttonBase = "inline-flex items-center justify-center rounded-lg font-medium transition-colors focus:outline-none focus:ring-2 focus:ring-offset-2 disabled:opacity-50 disabled:pointer-events-none"

// Variants
const variants = {
  primary: "bg-blue-600 text-white hover:bg-blue-700 focus:ring-blue-500",
  secondary: "bg-gray-100 text-gray-900 hover:bg-gray-200 focus:ring-gray-500",
  destructive: "bg-red-600 text-white hover:bg-red-700 focus:ring-red-500",
  ghost: "hover:bg-gray-100 text-gray-700",
}

// Sizes
const sizes = {
  sm: "h-8 px-3 text-sm",
  md: "h-10 px-4 text-sm",
  lg: "h-12 px-6 text-base",
}
```

### Card Component

```tsx
<div className="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden">
  <div className="p-6">
    <h3 className="text-lg font-semibold text-gray-900">Card Title</h3>
    <p className="mt-2 text-gray-600">Card description goes here.</p>
  </div>
  <div className="px-6 py-4 bg-gray-50 border-t border-gray-200">
    <button className="text-sm text-blue-600 hover:text-blue-800">
      Learn more →
    </button>
  </div>
</div>
```

### Input Field

```tsx
<div className="space-y-1">
  <label className="block text-sm font-medium text-gray-700">
    Email
  </label>
  <input
    type="email"
    className="
      w-full px-3 py-2 
      border border-gray-300 rounded-lg
      text-gray-900 placeholder-gray-500
      focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent
      disabled:bg-gray-100 disabled:cursor-not-allowed
    "
    placeholder="you@example.com"
  />
  <p className="text-sm text-gray-500">We'll never share your email.</p>
</div>
```

---

## Dark Mode

### Class Strategy

```tsx
// Add dark mode variants
<div className="
  bg-white text-gray-900
  dark:bg-gray-900 dark:text-white
">
  <h1 className="text-gray-900 dark:text-white">
    Title
  </h1>
  <p className="text-gray-600 dark:text-gray-400">
    Description
  </p>
</div>
```

### Configuration

```typescript
// tailwind.config.ts
export default {
  darkMode: 'class', // or 'media' for system preference
  // ...
}
```

---

## Custom Configuration

### Extend Theme

```typescript
// tailwind.config.ts
import type { Config } from 'tailwindcss'

export default {
  content: ['./src/**/*.{ts,tsx}'],
  theme: {
    extend: {
      colors: {
        brand: {
          50: '#f0f9ff',
          500: '#0ea5e9',
          900: '#0c4a6e',
        },
      },
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
      },
      spacing: {
        '18': '4.5rem',
      },
      animation: {
        'fade-in': 'fadeIn 0.5s ease-out',
      },
      keyframes: {
        fadeIn: {
          '0%': { opacity: '0' },
          '100%': { opacity: '1' },
        },
      },
    },
  },
  plugins: [],
} satisfies Config
```

---

## CSS Variables (Tailwind v4)

```css
/* globals.css - Tailwind v4 */
@import "tailwindcss";

@theme {
  --color-brand-500: #0ea5e9;
  --color-brand-600: #0284c7;
  
  --font-sans: "Inter", system-ui, sans-serif;
  
  --radius-lg: 0.75rem;
}
```

```tsx
// Usage
<div className="bg-brand-500 rounded-lg font-sans">
  Using custom theme values
</div>
```

---

## Performance Tips

### Avoid Dynamic Classes

```tsx
// ❌ Bad - Tailwind can't scan dynamic classes
<div className={`text-${color}-500`}>
  Content
</div>

// ✅ Good - Use complete class names
const colorClasses = {
  red: 'text-red-500',
  blue: 'text-blue-500',
  green: 'text-green-500',
}

<div className={colorClasses[color]}>
  Content
</div>
```

### Use @apply Sparingly

```css
/* ✅ OK for highly reused patterns */
.btn {
  @apply px-4 py-2 rounded-lg font-medium;
}

/* ❌ Avoid for one-off styles */
.my-specific-component {
  @apply flex items-center justify-between p-4 gap-4;
}
```

---

## Utility Combinations

### Common Patterns

```tsx
// Center everything
<div className="flex items-center justify-center">

// Stack with gap
<div className="flex flex-col gap-4">

// Truncate text
<p className="truncate">Long text...</p>

// Line clamp (2 lines)
<p className="line-clamp-2">Multi-line text...</p>

// Aspect ratio
<div className="aspect-video">

// Container
<div className="container mx-auto px-4">

// Visually hidden (accessible)
<span className="sr-only">Screen reader text</span>
```

---

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Dynamic class names | Use object maps with complete classes |
| Too many `@apply` | Keep utilities in markup |
| Not using design system | Define colors/spacing in config |
| Ignoring dark mode | Add `dark:` variants |
| Inconsistent spacing | Use Tailwind's spacing scale |
| Random class order | Follow consistent ordering |
