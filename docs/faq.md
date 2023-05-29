# Frequently Asked Questions (FAQ)

### Why not improve `@types/aframe` instead?
The goal of this project is to provide the best developer experience when working with A-Frame and TypeScript. To achieve this the typings in this project can differ from what they technically are or in a few cases even require the use of helper functions. This would not fit the DefinitelyTyped project.

Having our own provided typings also allows for faster iterations and including documentation directly in the typings.

### Do I need to use TypeScript? Can I just use the docs generator or the VS code extension?
The focus of the project is on using TypeScript. It's these typings along with TSDoc that enable a lot of the surrounding tooling. That isn't to say everything needs to be TypeScript. The following hybrid situations are all supported:

 * [Create typings](/guides/create/typings) ^:simple-typescript:^ for an existing A-Frame library written in JavaScript ^:simple-javascript:^
 * Publishing a library ^:simple-typescript:^ that others can use in their A-Frame project ^:simple-javascript:^
 * Using existing A-Frame libraries ^:simple-javascript:^ in your TypeScript A-Frame application ^:simple-typescript:^

The typings _might_ also work when _in_ a plain JavaScript project. This hasn't been explored and isn't the focus, but if you're interested in this do [reach out](/about/contact).

### Why does the generator use X?
The project is *opinionated* so the tools, frameworks and defaults are all chosen to "just work". A lot of the tools can easily be swapped out, and you're free to do so. The generator templates, however, will most likely not offer the user any choices in this regard to make testing and maintaining the project easier.
