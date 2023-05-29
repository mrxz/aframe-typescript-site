# Systems


=== "A-Frame + TypeScript :simple-typescript:"

    ``` ts
    import * as AFRAME from 'aframe';

    export const FooSystem = AFRAME.registerSystem('foo', {
        schema: {
            bar: {type: 'number'},
            baz: {type: 'string'}
        },

        init: function() {
            // Do something when system initializes.
        },

        tick: function(time, timeDelta) {
            // Do something on every scene tick or frame.
        }
    });

    declare module "aframe" {
        export interface Systems {
            "foo": InstanceType<typeof FooSystem>
        }
    }
    ```

=== "A-Frame :simple-javascript:"

    ``` js
    AFRAME.registerSystem('foo', {
        schema: {
            bar: {type: 'number'},
            baz: {type: 'string'}
        },

        init: function() {
            // Do something when system initializes.
        },

        tick: function(time, timeDelta) {
            // Do something on every scene tick or frame.
        }
    });
    ```