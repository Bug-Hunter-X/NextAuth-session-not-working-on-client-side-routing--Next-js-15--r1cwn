# NextAuth Session Issue on Client-Side Routing (Next.js 15)

This repository demonstrates a bug where NextAuth session data is not accessible after client-side navigation within a Next.js 15 application, despite using `unstable_getServerSession`. 

The problem occurs when navigating to the `/about` page from the `/` page.  The `/about` page uses `unstable_getServerSession` to check for authentication. However, after client-side navigation, the session object remains null, even if the user is logged in.

## Steps to Reproduce

1. Clone this repository.
2. Install dependencies: `npm install`
3. Run the development server: `npm run dev`
4. Navigate to `http://localhost:3000`
5. Navigate to the about page using the link. Observe the error.

## Expected Behavior

The `/about` page should display the user's email address if they are logged in. The session information should persist after client-side navigation.

## Actual Behavior

The `/about` page displays "Please sign in" even when the user is already logged in after client-side navigation.

## Solution

This issue is resolved by switching to `getServerSideProps` or `getStaticProps` for the `/about` page.