# Events

=== "A-Frame + TypeScript :simple-typescript:"

    ``` ts
    import * as AFRAME from 'aframe';

    declare module "aframe" {
        export interface EntityEvents {
            "eventname": DetailEvent<{degrees: number, source: Entity/* (1)! */}>,
        }
    }
    ```

    1.  The type parameter of DetailEvent represents the type of the `detail` property on the emitted events. They can be anything you want
