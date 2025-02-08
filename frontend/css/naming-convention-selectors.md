# Naming Convention (Selectors)

This naming convention relies on structured class names and meaningful hyphens (not using hyphens just to separate words). This helps to better communicate the relationships between classes.

The primary building blocks are utilities and components.

## Table of contents

- [Utilities](#utilities)
- [Components](#components)
  - [ComponentName](#componentname)
  - [ComponentName--modifierName](#componentname--modifiername)
  - [ComponentName-descendentName](#componentname-descendentname)
  - [ComponentName.is-stateName](#componentnameis-statename)

## Utilities

> [!Note]
> **Syntax:** `u-<utilityName>`

Low-level structural and positional traits. Utilities can be applied directly to any element within a component.
They should provide commonly used functionality, which will likely not change in the future.

> [!Warning]
> They should be used sparingly. We do not want to build a utility-class based system.

```css
/* Hide content visually, but provide it to screen readers */
.u-visuallyHidden:not(:is(:focus, :active)) {
    clip: rect(0 0 0 0);
    clip-path: inset(50%);
    height: 1px;
    overflow: hidden;
    position: absolute;
    white-space: nowrap;
    width: 1px;
}
```

## Components
> [!Note]
> **Syntax:** `<ComponentName>[-descendentName][--modifierName]`


The CSS responsible for styling a specific component in the design system. This has several benefits when reading and writing HTML
and CSS:
- It helps to distinguish between the classes for the root of the component, descendent elements, and modifications.
- It keeps the specificity of selectors low.
- It helps to decouple presentation semantics from DOM semantics.

### ComponentName

The component's name must be written in pascal case.

```css
.ButtonPrimary {
    /* … */
}
```

```html
<button class="ButtonPrimary">
    <!-- … -->
</button>
```

### ComponentName--modifierName
A component modifier is a class that modifies the presentation of the base component in some form (e.g., for a certain configuration of the component). 

Modifier names must be written in camel case and be separated from the component name by two hyphens. The class should be included in the HTML *in addition* to the base component class.

```css
.ButtonPrimary {
    /* … */
}

.ButtonPrimary--small {
    /* … */
}
```

```html
<button class="ButtonPrimary ButtonPrimary--small">
    <!-- … -->
</button>
```

> [!Tip]
> Not having modifier selectors nested, increases readability of a component.
> This also makes it easier to use code-folding to get a quick overview of which modifiers exist for a specific component.

### ComponentName-descendentName
A component descendent is a class that is attached to a descendent node of a component. It's responsible for applying styles directly to the descendent on behalf of a particular component. Descendent names must be written in camel case.

```html
<blockquote class="Quote Quote--large">
    <div class="Quote-text">
        <!-- … -->
    </div>
    <div class="Quote-footer">
        <div class="Quote-author">
            <img class="Quote-authorImage" src="…" alt="…">
            <p class="Quote-authorName">Aldous Huxley</p>
        </div>
        <cite class="Quote-source">Brave New World</cite>
    </div>
</blockquote>
```

> [!Important]
> In css files, descendants should not be nested inside their parent. They may only be nested inside their “root” component.
> Otherwise the layout of the html would be strongly coupled with the styling of a particular element.
> We want to be able to style the `.Quote-author` regardless of if it is inside the `.Quote-footer` or at some other place in our
component.

```css
.Quote {
 /* … */

 .Quote-text { /* … */ }

 .Quote-footer { /* … */ }

 .Quote-author { /* … */ }

 .Quote-authorImage { /* … */ }

 .Quote-authorName { /* … */ }

 .Quote-source { /* … */ }
}

.Quote--large {
    /* … */
}
```

### ComponentName.is-stateName

Use `is-stateName` to reflect changes to a component's state. The state name must start with `is-` and use a descriptive name in
camel case.

These classes should never be styled on a global level. They should always be scoped to a component. This means that the same state names can be used in multiple components, but every component must define its own styles for the state.

```css
.ButtonPrimary {
    /* … */

    &.is-loading { /* … */ }
}
```
```css
.InputSingleline {
    /* … */

    &.is-loading { /* … */ }
}
```

```html
<button class="ButtonPrimary is-loading">
    <!-- … -->
</button>
```