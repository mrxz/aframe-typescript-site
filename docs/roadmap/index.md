# Roadmap
The project is currently in an **Alpha** phase. If you're interested in trying it out or learning more about it, please reach out (social links in footer below). If you'd rather try things out on your own, feel free to do so. Any feedback is greatly appreciated.

### 0.8 Alpha
The 0.8.x versions are part of the alpha phase. The goal of this phase is to get all elements of aframe-typescript in a functional state, so that it can be thoroughly tested and experimented with. Since it's likely that things might still change significantly, it's not intended for production use (yet)

| Component | Goal |
| --------- | -------- |
| aframe-types | <ul><li>Typings for all A-Frame core components, systems, primitives, shaders and geometries</li><li>Documentation for all components, systems and properties available</li><li>Handling of dynamic schema in components and systems</li></ul> |
| typescript-helpers | <ul><li>Helpers for common A-Frame patterns (IIFE methods, merging definitions)</li></ul> |
| docs-generator | <ul><li>Parsing of TsDoc (using TypeDoc) and converting to intermediate representation</li><li>Generating basic reference pages for Components, Systems and Primitives</li></ul> |
| generators | <ul><li>Generator for an A-Frame TypeScript app (dev, build, docs)</li><li>Generator for an A-Frame TypeScript library (dev, build, docs, publish)</li></ul> |
| vscode-extension | <ul><li>Basic auto completion</li><li>Hover information in HTML files (primitives and components)</li><li>Jump to definition from HTML to TypeScript</li></ul> |

### 0.9 Beta
Once the core elements are solidified (specifically the typings) the project moves into the Beta phase. At this point the main typings and `aframe-typescript` helpers shouldn't change much. Projects can start using A-Frame TypeScript and publishing typings for their A-Frame libraries/components. The focus of the project becomes improving the tooling, developer experience and fixing any bugs encountered during this phase before the stable release.

| Component | Goal |
| --------- | -------- |
| aframe-types | <ul><li>Typings for popular and commonly used A-Frame components, systems, primitives, shaders and geometries</li></ul> |
| docs-generator | <ul><li>Embedded live examples (tentative)</li><li>Cross library references/linking (tentative)</li></ul> |
| generators | <ul><li>Expand app generator with testing setup (unit and integration)</li><li>Expand lib generator with testing setup (unit and integration)</li></ul> |
| vscode-extension | <ul><li>Error checking (unknown components, incorrect types, etc...)</li><li>Syntax highlighting for component attribute values (`key: value, texture: url(./tex.png)`)</li></ul> |

### 1.0 Stable
Stable releases won't see many changes to the typings or helpers (for backwards compatibility). Typings will be updated to match newer A-Frame and, by extension, Three.js versions. TypeScript updates might also be incorporated, though on the condition that it doesn't break already published typings.

The surrounding tooling (generators, docs-generator and vscode-extension) will be continuously improved by fixing bugs and expanding functionality. The scope of the project might also be expanded at this point to facilitate integrations with popular frontend frameworks.


## Past releases
For past releases, including detailed list of changes, see the [Changelog](../changelog.md).

<style>
    .md-content ul > li {
        padding-left: 0.5em;
    }
    .md-content ul > li::marker {
        content: '✅';
    }
</style>