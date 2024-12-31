# Dynamically Generated Classes Removed by PurgeCSS in Tailwind CSS

This repository demonstrates a common issue encountered when using Tailwind CSS with dynamic content.  Tailwind's PurgeCSS feature optimizes the CSS by removing unused classes, but this can inadvertently remove classes generated dynamically during runtime.

## The Problem

When Tailwind's purge process runs, it analyzes your templates and removes any CSS classes that aren't used. However, if you generate classes based on user interactions or data changes (e.g., conditional rendering), those classes might be removed even though they're used later.

## Reproducing the Issue

1. Clone this repository.
2. Run `npm install`.
3. Run `npm run dev`.
4. Observe that the dynamically added background colors don't apply because the PurgeCSS process removed those classes.

## Solution

There are several approaches to solve this issue:

* **Whitelist classes:**  Manually add the dynamically generated class names to the `purge` configuration in your `tailwind.config.js` file. 
* **Use safelist:** If you know some potential classes, use `safelist` to prevent the PurgeCSS from removing them.
* **Disable PurgeCSS:**  Completely disable PurgeCSS if you are generating a huge number of dynamic classes. This is generally not recommended due to the size impact on the CSS file.
* **Runtime-only CSS:** Use CSS directly in the runtime, without Tailwind classes. This is not an ideal solution in most cases.

This repository illustrates the problem and provides a solution using the `safelist` feature. Refer to the `bugSolution.js` file for an example of how to fix it.

