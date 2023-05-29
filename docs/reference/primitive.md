# Primitives

=== "A-Frame + TypeScript :simple-typescript:"

    ``` ts
    import * as AFRAME from 'aframe';

    export const FooPrimitive = AFRAME.registerPrimitive('foo', {
        defaultComponents: {
            "foo": { bar: 42 },
        },
        mappings: {
            baz: 'foo.baz',
        }
    });

    declare module "aframe" {
        export interface Primitives {
            "foo": typeof FooPrimitive /* (1)! */
        }
    }
    ```

    1.  **Note:** in constrast to systems and components the type is specified here, _not_ the `InstanceType<typeof FooPrimitive>`!

=== "A-Frame :simple-javascript:"

    ``` js
    AFRAME.registerPrimitive('foo', {
        defaultComponents: {
            "foo": { bar: 42 },
        },
        mappings: {
            baz: 'foo.baz',
        }
    });
    ```