# Design principles

Component systems are focused on improving the authoring experience for
component-based development.

A component-based system allows for the implementation and composition of
loosely coupled, independent units into well-defined composite objects.

1. [Modularity](#modularity)
3. [Composition and configuration](#composition-and-configuration)
4. [Loose coupling](#loose-coupling)
5. [Soft encapsulation](#soft-encapsulation)
6. [Documentation](#documentation)

## Modularity

Each component should have a single focus and contain everything necessary to realise a specific part of the UI. 
Components may contain HTML, CSS, JavaScript, and associated assets without making assumptions about the outer rendering context.

## Composition and configuration

Composability is concerned with the inter-relationships of components.
Composable systems have components that can be assembled in various combinations, as required.

Components do not have direct influence over each other.
Configuration is done via interfaces that are provided and used by components.

## Loose coupling

Components should not directly modify the presentation or behaviour of their dependencies. 
Relying on interfaces and events for inter-component communication results in a loose coupling.

Attempting to reuse too much code across components can increase their coupling.
Isolation is more important than avoiding the repetition of superficially similar code.

## Soft encapsulation

The implementation of a component should not be exposed to other components.

> [!Note]
> For example:
> Your component should not leak styles into other components.

Complexity is a significant problem for large, adaptive applications. 
The more you can reduce the entanglement of your components, the easier it is to reason about the system.

## Documentation

Write small, independent components that are well documented to describe how
the components should be used, and why specific CSS properties are needed in
the implementation. 

> [!Important]
> Do not assume that CSS is self-documenting.
