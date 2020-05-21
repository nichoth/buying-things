https://www.netlify.com/blog/2020/04/13/learn-how-to-accept-money-on-jamstack-sites-in-38-minutes/?utm_source=blog&utm_medium=stripe-jl&utm_campaign=devex

You can sell products on Jamstack sites using Stripe Checkout to process payments and Netlify Functions to securely create Checkout sessions.

This example uses no statix site generator like 11ty.

-------------------

Use the netlify cli. It allows us to run Netlify Functions locally.
`npm i -D netlify-cli`. This exposes the `ntl` command: `npx ntl dev`. The file `netlify.toml` tells the CLI where the files are. 

--------------------

>  If we were using a static site generator like 11ty, Scully, or any of the many options out there, it might make more sense to pre-render the products instead of loading them at run-time. **To avoid build steps for the frontend code in this demo, we opted for a plain JavaScript async approach.**

> Why is the data in the functions folder? Netlify deploys functions to a separate environment as part of the build, so we aren’t able to reference files outside the functions directory in production.

> Now that we have data available, let’s create `functions/get-products.js` to load the data and return it for use in our frontend.

For Netlify to deploy our serverless functions, we need to tell it where they’re located. To do this, we need to modify netlify.toml with a functions setting and add our functions directory as the value.

Run `npx ntl dev` then visit `http://localhost:8888/.netlify/functions/get-products` to run the function.

To load the product data into the frontend of our site, we need to add some client-side JavaScript. See `/public/js/load-products.js`

This function uses the built-in Fetch API to load the response from our serveless function

------------------------------

To create the markup for our products, we’re going to use the HTML <template> tag. We can define product markup in a component-like fashion.

----------------------------

todo:

## Connect to Netlify and set up automatic deployments using the Netlify CLI
Create a new Netlify site using the command line: `ntl init`

Open netlify dashboard: `ntl open`
Open the site: `ntl open:site`

## env variables
third-party API tokens and secret things

the publishable key and the secret key for our Stripe account


