# TypeScript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'intéret de TypeScript dans l'IDE ✔️
- les types de bases ✔️
- comment et pourquoi étendre une interface ✔️
- les classes et les decorators ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```tsx
// Button.jsx
import React, {FunctionComponent, ReactNode} from "react";

// déclaration des tags autorisés dans le prop as
type AllowedComponents = 'a' | 'button'

type Variant = "common" | "light" | "dark"
// déclaration des props du Button
interface Props {
    children: ReactNode, // HTML, components, string, numbers, etc
    className?: string,
    rounded?: boolean,
    as?: AllowedComponents,
    href?: string,
    variant?: Variant
}

// declarations des variantes en tailwind
const styles: Record<Variant, string> = {
    common: `font-bold shadow-2xl cursor-pointer hover:scale-105 transition-transform ease-out inline-block p-4`,
    dark: `bg-dark-shades text-light-shades`,
    light: `bg-light-shades text-dark-shades`
}

// Déclaration du composant, déstructuration des props
const Button: FunctionComponent<Props> = ({children, variant, className, rounded, as, href}) => {
    const Component = as || 'button' // Component contient le tag HTML
    if (!variant) variant = 'dark'
    return (
        <Component href={href} className={`${styles.common} ${styles[variant]} ${rounded ? 'rounded-2xl' : ''} ${className}`}>
            {children}
        </Component>
    )
}

Button.defaultProps = {
    className: '',
    rounded: false,
    variant: "dark"
}

export default Button
```

### Utilisation dans un projet ✔️

[lien github](https://github.com/Hugo-M33/portfolio-2022/)

Description : Application portfolio Next.JS

### Utilisation en production si applicable ❌

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌

Description :

## 🌐 J'utilise des ressources

### Type Challenges

- https://github.com/type-challenges/type-challenges
- Challenges qui consistent à recoder les fonction typescript, et d'autres

## 🚧 Je franchis les obstacles

### Point de blocage ❌

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌
- J'ai fait une [présentation](...) ❌
