First I run (imported express from npm),

`deno run -A --node-modules-dir main.ts`

And everything is fine, node_modules dir created locally.

After that i changed the import path of express to locally (from node_modules)

EDIT: It was actually my silly mistake,

I dint explicitly specified the index.js file in express folder...

Here's the following path

`./node_modules/.deno/express@4.18.2/node_modules/express`
 
When i ran it, It just throws Access Denied Error (5)

So that was my mistake,

That problem solved when i tried with providing index.js in Path,

`./node_modules/.deno/express@4.18.2/node_modules/express/index.js`

But this throws an another error Which `there is no default exported member`

I guess this error basically comes from node's require() function is still used on the file...

I think that deno internally transpile the node's require() call.

But we cant import it here, then there is no point to provide --node-modules-dir for these type of non-esm packages. 

This is a issue, Thanks for Responding.
