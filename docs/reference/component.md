# Components
A-Frame allows creating your own components. This is done using the `registerComponent` method.
In aframe-typescript this is no different, but

=== "A-Frame + TypeScript :simple-typescript:"

    ``` ts
    import * as AFRAME from 'aframe';

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

## Lax and Strict components
By default components that are registered are "lax". With lax components you still get typing based on the schema, but the `this` type of a component allows new properties to be added inside of the function. This is commonly done in the `init()` function to define some instance variables like event handlers. The downside of this approach is that TypeScript can't infer any types for these properties. So anything initialized this way in `init()` will appear as `any` type in the other function.

A-Frame TypeScript provides a helper to define a "strict" component instead. This is done using the `strict` helper. See the comparison below between a (standard) "lax" component and a "strict" component:

=== "Lax Component :simple-typescript:"

    ``` ts
    import * as AFRAME from 'aframe';
    import * as THREE from 'three';

    export const FooComponent = AFRAME.registerComponent('foo', {
        schema: {
            color: {type: 'color'},
        },

        init: function() {
            // Create a new instance of THREE.Color to use during update calls
            this.color = new THREE.Color();
        },

        update: function(oldData) {
            // Check if the color property has changed
            if(oldData.color !== this.data.color) {
                // Parse the color and dim it
                this.color.set(this.data.color).multiplyScaler(0.5);
                // Apply the color to the material component
                this.el.setAttribute('material', 'color', this.color);
            }
        }
    });
    ```

=== "Strict Component :simple-typescript:"

    ``` ts
    import * as AFRAME from 'aframe';
    import * as THREE from 'three';
    import { strict } from 'aframe-typescript'; // (1)!

    export const FooComponent = AFRAME.registerComponent('foo', /* (2)! */strict<{
        /* Color object used for parsing incoming color values */
        color: THREE.Color /* (3)! */
    }>().component({
        schema: {
            color: {type: 'color'},
        },

        init: function() {
            // Create a new instance of THREE.Color to use during update calls
            this.color = new THREE.Color();
        },

        update: function(oldData) {
            // Check if the color property has changed
            if(oldData.color !== this.data.color) {
                // Parse the color and dim it
                this.color.set(this.data.color).multiplyScaler(0.5);
                // Apply the color to the material component
                this.el.setAttribute('material', 'color', this.color);
            }
        }
    })); /* (4)! */
    ```

    1.  Helpers are part of the `aframe-typescript` package
    2.  Don't be fooled by the formatting, it's just two method invocations `strict<{...}>().component({...})`
    3.  Since each property is now specified, documentation strings can be provided for them
    4.  Don't forget the additional closing brace!
