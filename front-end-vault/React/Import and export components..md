## Import and export components.
When we are in the process of splitting our components in different file, we need to export or  import those components.

### The root component file
Our root component is usually the App.js filte. If you use a framework with file-based routing, such as Next.js, the root component will be different for every page.

### Exporting and importing a component
Steps to split the components.
1. Make a new JS file.
2. Export yout function component using __Default__ or __named__ exports.
3. Import it the file where you'll use the component. Again using the __default__ or __named__ exports/imports.

### Default vs named exports
A file can have no more than one default export, but it can have as many named exports.

![[default_named_exports_differences.png]]

![[default_named_import_export_table.png]]

Always give meaningful names to your component functions.
Components without names `export default () => {}`, are discouraged because they make debugging harder.