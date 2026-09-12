# spec-pax

The complete specification and portable decoding reference for **PAX numeric file
format version 0**: progressively stream a 3D scene, reuse early geometry and
texture data, and render before the full asset arrives.

Read [SPECIFICATION.md](SPECIFICATION.md) for the binary header, packet directory,
checksums, geometry codecs, texture tiles and GPU mips, extension dependencies,
random access, completion rules and fidelity boundaries.

- [convert-pax](https://github.com/AndreBaltazar8/convert-pax): converter and size/fidelity verification.
- [three-pax](https://github.com/AndreBaltazar8/three-pax): Three.js loader and runnable comparison samples.

```sh
npm ci
npm test
```

The numeric wire version lives in a uint32 at byte offset 4. It is currently **0**;
package semantic versions do not identify the file format. Legacy `PAX1` files
must be reconverted. This is a research format, not an established standard.

`src/` contains portable decoding algorithms; `fixtures/` contains a small generated
morph fixture with conversion proof metadata. The converter enforces a maximum
whole-file size of 105% of the original input and rejects inputs that cannot fit.
Final decoded data is lossless within the [defined profile](SPECIFICATION.md#10-encoder-profile-and-fidelity);
intermediate stages are approximate. Animation clips arrive in the bootstrap.

Code and generated fixture: MIT.
