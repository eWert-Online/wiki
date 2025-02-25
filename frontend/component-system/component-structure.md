# Component Structure

There are many different ways to approach the creation of a design system. When it comes to the structure of a design system, it's important to choose terminology that avoids confusion. 

While "Atomic Design" is a popular methodology, in my experience, its strict hierarchical structure falls apart in some cases.

I had some good experience with the followng structure:

1. [Foundations](#foundations)
2. [Components](#components)
3. [Patterns](#patterns)
4. [Screens](#screens)

## Foundations

Foundations are the smallest "building blocks" of the design system. They are not yet actual components that can be placed somewhere on a page.
They more so lay the foundation of the desin-system.

Typical items in this category are: colors, fonts, icons, spacings and a grid definition.

## Components

Components are reusable pieces of the UI, that do not make any assumption over the context in which they are used.

Every component can be used in another component, as long as the resulting component is reusable in any context.

Examples include: buttons, images, headlines, input-fields, collapsibles, modals.

## Patterns 

Larger, complex components or groups of components. These elements are not reusable in any context. They are built to fulfill a specific requirement on a page.

Examples include: headers, footers.

## Screens

Page-level objects that place components into a layout and articulate patterns.

Examples include: homepage, article page, product detail page.
