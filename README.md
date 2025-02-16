# React Router Dom Catch-All Route Interception Bug

This repository demonstrates a subtle bug in React Router v6 where the catch-all route (`*`) unexpectedly intercepts other, correctly defined routes.  The issue manifests when the catch-all route is placed before more specific routes within the `<Routes>` component.

## Bug Description

The provided code shows a simple React application with routes for '/about' and a catch-all route for '/*'.  Despite the more specific '/about' route, navigation to '/about' results in the catch-all route being triggered, leading to a '404 Not Found' instead of the expected 'About' page. This happens because React Router processes routes sequentially; the catch-all route is always the first to match.

## Solution

The solution involves ensuring that the catch-all route is placed last within the `<Routes>` component.  This ensures that it only matches paths which are not already matched by earlier, more specific routes.