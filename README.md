# spec-pax

Specification and reference decoder for **PAX v0**, a 3D asset format that reuses
initial geometry and texture data as detail arrives. Animation clips load in the
bootstrap.

Read [SPECIFICATION.md](SPECIFICATION.md) for the binary layout, packets,
checksums, codecs, extensions, random access and completion rules.

## Format

- The file version is a `uint32` at byte offset 4, currently **0**. Package versions
  are separate. Legacy `PAX1` files require reconversion.
- Previews are approximate. Final data is lossless within the
  [defined profile](SPECIFICATION.md#10-encoder-profile-and-fidelity).
- The converter limits the complete file to **105% of the source size** and rejects
  inputs that cannot fit.
- PAX is experimental, not an established standard.

## Reference implementation

`src/` contains decoding algorithms. `fixtures/` contains a generated morph asset
and reconstruction hashes.

```sh
npm ci
npm test
```

## Related projects

- [convert-pax](https://github.com/AndreBaltazar8/convert-pax): glTF/GLB converter.
- [three-pax](https://github.com/AndreBaltazar8/three-pax): Three.js loader and samples.
- [blender-pax](https://github.com/AndreBaltazar8/blender-pax): Blender import/export.

Code and generated fixture: [MIT](LICENSE).
