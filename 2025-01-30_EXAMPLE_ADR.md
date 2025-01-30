# Procuring a React component library

Date: 21/12/2022

## Status

Proposed

## Context

Currently, the new platform's web application UI, implements _almost_ all of its components from the ground up. This approach gave us a lot of creative freedom while designing and implementing the building blocks of our application. Unfortunately, it also hinders the development process, by adding extra complexity to the implementation, and increasing the time to market. The extra complexity also means added risk, as we need to maintain and evolve the components to ensure they are accessible, extendable, and performant.

## Decision

We have come to a decision to procure a React component library, that would provide us with a standard set of components, that we can use to build our application.

We have decided to go ahead with implementing `Mantine` as our component library. The main reason for this decision is that with `Mantine` we would still be able to customise the look and feel of the components to our needs. And with the vast array of components that we would have access to, we would be able to build our application faster, and with less risk.

### Requirements

The component library should:

- work in a framework such as Next.js, function in a Server Side Generated page, and be compatible with
  our current stack.
- be open source, well documented, and have a permissive license.
- be well tested.
- have typescript support out of the box.
- be actively maintained, and have a community of developers.
- be accessible, and have a good track record of accessibility.
- be performant, and have a good track record of performance.
- be extendable, and allow us to customise the components to our needs.
- be themable, and allow us to customise the components in accordance
  with our design system.

## Options and Consequences

During the R&D phase we considered many options, and narrowed them down to the following:

- [Mantine](https://mantine.dev/)
- [Radix UI](https://www.radix-ui.com/)

### Evaluation

#### Mantine

As well as meeting our requirements, `Mantine` component library comes with over _120_ components that cover a wide range of use cases. The `Mantine` family of products also include over _40_ hooks, packages to help with dates, forms, d&d, and more.

#### Radix UI

`Radix UI` is a collection of low-level, unstyled React components that are designed to be used to build your own design system. Even though `Radix UI` does not come with a lot of components out of the box, it does provide a solid foundation for building our own components.

### Implementation

The `Mantine` library will be installed in `{redacted package}` which is a shared package in the `{redacted repo}` monorepo. `{redacted package}` will export themed and customised `Mantine` components to be used by `{redacted repo}` micro-sites.

We'll take an incremental approach to implementing the component library. We'll start by creating a custom `Mantine` theme that would be used to style the components in accordance with our current design system. We'll then start replacing the components that we have already built, with the `Mantine` components. Any new components/screens built during this gradual adoption will be built using the `Mantine` components.

### Governance

The component library will be governed by the frontend guild. The guild will be responsible for ensuring that the component library is maintained, and that the components are kept up to date with the latest versions of the library. As the `{redacted package}` will be consumed by multiple teams, it is important that any breaking changes, and changes to the `Mantine` component props is avoided. Extending the components to meet our needs, and adding new components should be done in a way that does not break the existing components.

### Deployment

There are currently no plans to publish the `{redacted package}` package to npm, or any other registry where it can be consumed by other `{redacted company name}` applications that are built outside of the monorepo where `{redacted package}` lives. However in the future, if we decide to publish the package, we would need to ensure that the package is versioned, a changelog is created, And a CI/CD pipeline is created to build and publish this package. The package would also need to be documented. Whether this package is made open source or not, is still to be decided.

### Documentation

Storybook is to be used as the main source of truth for the `{redacted package}` documentation. Storybook will also act as the main source of truth for design tokens, and the design system. However, to avoid duplication of the source of truth and avoid the risk of falling out of sync, we will use the [Mantine documentation](https://mantine.dev/pages/getting-started/) for the `Mantine` components that we use. We will refer to the `Mantine` documentation for the props, and how to use the components. Custom components that we build from scratch or on top of what `Mantine` provides will be documented in Storybook.

### Testing

The `{redacted package}` package will be tested using [Jest](https://jestjs.io/), and [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/). The tests will be run as part of the CI/CD pipeline, and will be required to pass before a PR can be merged.

### Consequences

- The main consequence of this decision is that we will be able to build our application faster, and with less risk.
- We will be able to focus on the business logic, and the features of the application, instead of building the building blocks of the application.
- `Mantine` is accessible out of the box.
- While this decision will benefit us in the long run, it will also mean that we will need to spend time migrating the existing components to the new component library.
- We will need to ensure that the `Mantine` components are kept up to date with the latest versions of the library.

## Future work

- The current design system used in the application has not had a design review, therefore, the custom `Mantine` theme will need to be updated to reflect the latest design system once a design review has been conducted. This can be postponed until the ongoing company wide brand refresh is completed.
