# How to Add Extra Parameters

This guide explains how to extend button styles in your project with **Neuromorphism** and **Minimalist** design parameters. Follow the steps below to customize button shadows and border radii using CSS and JavaScript.

---

## Neuromorphism

### Extra Fields: Button Shadow

Add the following CSS to your `globals.css` or appropriate stylesheet:

```css
@layer utilities {
  .btn-shadow {  
    @apply shadow-[0_4px_0_0_hsl(var(--btn-shadow))];
  }

  .btn-shadow-active {  
    @apply shadow-[0_2px_0_0_hsl(var(--btn-shadow))];
  }

  .btn-border-color {
    border-color: hsl(var(--btn-shadow));
  }
}
```

### Apply Shadows to Button

Update the Button component using cva to integrate the new shadow styles:

```javascript
const buttonVariants = cva(
  "inline-flex items-center justify-center gap-2 whitespace-nowrap text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 [&_svg]:pointer-events-none [&_svg]:size-4 [&_svg]:shrink-0",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive:
          "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        outline:
          "border border-input bg-background hover:bg-accent hover:text-accent-foreground btn-shadow active:btn-shadow-active btn-border-color",
        secondary:
          "bg-secondary text-secondary-foreground hover:bg-secondary/80 border btn-shadow active:btn-shadow-active btn-border-color",
        ghost: "hover:bg-accent hover:text-accent-foreground",
        link: "text-primary underline-offset-4 hover:underline",
      },
      size: {
        default: "h-10 px-4 py-2",
        sm: "h-9 px-3",
        lg: "h-11 px-8",
        icon: "h-10 w-10",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
)
```

### Update Border Radius
```css
/* Previous */
--radius: 0.5rem;

/* New */
--radius: 0.25rem;
```

---

## Minimalist

### Add Button Border Radius Parameter

Define a utility class for customizable button border radius:
```css
@layer utilities {
  .btn-border-radius {
    @apply border rounded-full
  }
}
```

### Apply to Button Component

In your <Button.tsx> file, add the border radius utility class:
```javascript
const buttonVariants = cva(
  "inline-flex items-center justify-center gap-2 whitespace-nowrap btn-border-radius text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 [&_svg]:pointer-events-none [&_svg]:size-4 [&_svg]:shrink-0",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive: "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        ...
      },
      size: {
        default: "h-10 px-4 py-2",
        sm: "h-9 px-3",
        lg: "h-11 px-8",
        icon: "h-10 w-10",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
)
```


