# Components
A-Frame allows creating your own components. This is done using the `registerComponent` method.
In aframe-typescript this is no different, but

=== "A-Frame :simple-javascript:"

    ``` js
    AFRAME.registerComponent('foo', {
        schema: {
            bar: {type: 'number'},
            baz: {type: 'string'}
        },

        init: function() {
            // Do something when component first attached.
        },

        tick: function(time, timeDelta) {
            // Do something on every scene tick or frame.
        }
    });
    ```

=== "A-Frame + TypeScript :simple-typescript:"

    ``` ts
    export const FooComponent = AFRAME.registerComponent('foo', {
        schema: {
            bar: {type: 'number'},
            baz: {type: 'string'}
        },

        init: function() {
            // Do something when component first attached.
        },

        tick: function(time, timeDelta) {
            // Do something on every scene tick or frame.
        }
    });

    declare module "aframe" {
        export interface Components {
            "foo": InstanceType<typeof FooComponent>
        }
    }
    ```
