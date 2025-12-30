# Admiral

Admiral is a frontend framework for creating back office applications using React. It provides out-of-the-box components and tools that make developing an admin interface easy and fast.

## Features

-   **UI Components**: A comprehensive set of reusable UI components like tables, forms, drawers, and more.
-   **CRUD Operations**: Built-in support for Create, Read, Update, Delete operations with customizable interfaces.
-   **Data Providers**: Flexible data provider system for connecting to various backends.
-   **Authentication**: Integrated authentication and authorization features.
-   **Theming**: Customizable themes and styling options.
-   **Localization**: Support for multiple languages.
-   **Responsive Design**: Mobile-friendly components and layouts.

## Quick Start

```bash
npm install && npm run dev
```

## Deployment

### Building the Library

To build Admiral as a library for production:

```bash
npm run build:lib
```

This will generate the library files in the `lib/` directory.

### Building the Demo Application

To build the demo application:

```bash
npm run build
```

### Publishing to npm

If you're contributing or maintaining the project:

1. Ensure you're logged in to npm: `npm login`
2. Publish the package: `npm publish`

### Deploying Your Application

When using Admiral in your project, build your application as usual with your bundler (e.g., Vite, Webpack). Ensure all peer dependencies are installed.

For production deployment, follow standard React deployment practices. For example, with Vercel or Netlify, simply connect your repository and deploy.

### Usage Example

After deploying the application, access the admin UI at:
http://localhost:3000

Login using valid admin credentials to manage users and settings.

## Usage Examples

### Installation

```bash
npm install admiral
```

### Basic Setup

```tsx
import React from 'react'
import { Admin, Resource } from 'admiral'
import { dataProvider } from './dataProvider'
import { authProvider } from './authProvider'

const App = () => (
    <Admin dataProvider={dataProvider} authProvider={authProvider}>
        <Resource name="users" list={UserList} create={UserCreate} edit={UserEdit} />
    </Admin>
)

export default App
```

### Using UI Components

```tsx
import { Button, Table, Drawer } from 'admiral'

const MyComponent = () => (
    <div>
        <Button view="primary">Click me</Button>
        <Table columns={columns} dataSource={data} />
    </div>
)
```

### CRUD Operations

Admiral provides built-in CRUD components. See the `pages/` directory in this repository for comprehensive examples, including:

-   Basic CRUD: `pages/base-crud/`
-   Advanced Edit Pages: `pages/advanced-edit-page/`
-   Custom Drawers: `pages/crud-with-custom-drawer/`
-   Bulk Actions: `pages/bulk-actions/`

### Theming

```tsx
import { ThemeProvider, useTheme } from 'admiral'

const App = () => <ThemeProvider theme="light">{/* Your app content */}</ThemeProvider>
```

## API Reference

Admiral exports a wide range of components, hooks, and utilities. Below is an overview of the main modules:

### UI Components

-   **Badge**: Status indicators
-   **Button**: Action buttons with various styles
-   **Checkbox**: Selection controls
-   **ColorPicker**: Color selection tool
-   **DatePicker**: Date and time selection
-   **Drawer**: Slide-out panels
-   **Input**: Text input fields
-   **Menu**: Navigation menus
-   **Pagination**: Data pagination
-   **Select**: Dropdown selections
-   **Spin**: Loading indicators
-   **Switch**: Toggle switches
-   **Table**: Data tables with sorting and selection
-   **Tabs**: Tabbed interfaces
-   **Textarea**: Multi-line text input
-   **Tooltip**: Hover information
-   **Upload**: File upload components

### Form Components

-   Form fields, validation, and submission utilities

### Data Table

-   Fields and actions for data tables

### Filters

-   Filtering components and locale support

### Actions

-   CRUD action handlers

### Admin

-   Main Admin component for setting up the application

### Data Provider

-   `useDataProvider` hook for data operations
-   Interfaces for custom data providers

### Authentication

-   `useGetIdentity` hook
-   Auth provider interfaces

### CRUD

-   CRUD-related components and interfaces

### Navigation

-   `useNav` hook for navigation

### Theme

-   `useTheme`, `useThemeVars` hooks
-   Theme types and presets

### Utils

-   Various utility hooks

For detailed API documentation, including props and types, refer to the TypeScript definitions in the source code or generated documentation.

## Backend API Reference

The UI communicates with a backend API.

Base URL:
http://localhost:8080/api

Example endpoint:
GET /users – Fetch list of users

## Best Practices

### Component Usage

-   Use semantic component names and consistent prop naming.
-   Leverage the built-in theming system for consistent styling.
-   Implement proper error handling in data operations.

### Performance

-   Use pagination for large datasets to improve performance.
-   Implement lazy loading for components when possible.
-   Optimize re-renders by using React.memo for custom components.

### Security

-   Always validate user inputs on both client and server sides.
-   Use HTTPS for all communications.
-   Implement proper authentication and authorization checks.

### Accessibility

-   Ensure components are keyboard navigable.
-   Provide appropriate ARIA labels and roles.
-   Test with screen readers and other assistive technologies.

### Code Organization

-   Separate business logic from presentation components.
-   Use custom hooks for reusable logic.
-   Follow React best practices for state management.

### Data Management

-   Implement proper error handling for API calls.
-   Use optimistic updates for better UX.
-   Cache data appropriately to reduce unnecessary requests.

### Configuration and Deployment

-   Use environment variables for sensitive configuration
-   Do not commit `.env` files to version control
-   Use production-ready build commands for deployment

## Troubleshooting Guide

### Common Issues

#### Build Errors

-   **Issue**: TypeScript compilation errors

    -   **Solution**: Ensure all peer dependencies are installed. Run `npm install` and check TypeScript versions.

-   **Issue**: Module not found errors
    -   **Solution**: Verify the import paths. Admiral uses named exports, so import like `import { Button } from 'admiral'`.

#### Runtime Errors

-   **Issue**: Components not rendering

    -   **Solution**: Check if the ThemeProvider is wrapping your app. Ensure React version compatibility (React 17+).

-   **Issue**: Data not loading

    -   **Solution**: Verify your data provider configuration. Check network requests in browser dev tools.

-   **Issue**: Authentication not working

    -   **Solution**: Ensure authProvider is correctly implemented and passed to the Admin component.

-   **Issue**: Application not starting

    -   **Solution**: Ensure dependencies are installed. Verify environment variables are set correctly.

-   **Issue**: API connection issues
    -   **Solution**: Confirm the backend service is running. Check the API base URL configuration.

#### Styling Issues

-   **Issue**: Styles not applying

    -   **Solution**: Import the CSS file: `import 'admiral/style.css'`. Check for CSS conflicts.

-   **Issue**: Theme not changing
    -   **Solution**: Use the ThemeProvider and ensure theme names match available presets.

#### Performance Issues

-   **Issue**: Slow rendering

    -   **Solution**: Implement pagination for large lists. Use React DevTools Profiler to identify bottlenecks.

-   **Issue**: Memory leaks
    -   **Solution**: Properly clean up event listeners and subscriptions in useEffect hooks.

### Getting Help

-   Check the [Issues](https://github.com/dev-family/admiral/issues) page on GitHub for similar problems.
-   Provide a minimal reproduction case when reporting bugs.
-   Include your environment details (Node version, React version, etc.) in bug reports.

## License

MIT © celvios
