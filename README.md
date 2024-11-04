# @swc/core@1.8.0 incompatibility with @swc/plugin-styled-components@4.0.0

You will need node and pnpm.

```shell
corepack enable
pnpm i
pnpm exec swc index.js --out-file out.js
```

Expect to see a warning similar to this:

```
thread '<unnamed>' panicked at /home/runner/.cargo/registry/src/index.crates.io-6f17d22bba15001f/swc_plugin_proxy-3.0.0/src/memory_interop/read_returned_result_from_host.rs:110:10:
Returned value should be serializable: wasm plugin bytecheck failed "check bytes error: check failed for tuple struct member 0: check failed for struct member source_file: check failed for enum tuple variant Some: check failed for tuple struct member 0: check failed for struct member lazy: invalid tag for enum: 131"
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
thread '<unnamed>' panicked at /Users/runner/.cargo/registry/src/index.crates.io-6f17d22bba15001f/swc-4.0.0/src/plugin.rs:169:14:
failed to invoke plugin: failed to invoke plugin on 'Some("index.js")'

Caused by:
    0: failed to invoke `@swc/plugin-styled-components` as js transform plugin at @swc/plugin-styled-components
    1: failed to run Wasm plugin transform. Please ensure the version of `swc_core` used by the plugin is compatible with the host runtime. See the documentation for compatibility information. If you are an author of the plugin, please update `swc_core` to the compatible version.

                       Note that if you want to use the os features like filesystem, you need to use `wasi`. Wasm itself does not have concept of filesystem.

                       https://swc.rs/docs/plugin/selecting-swc-core

                       See https://plugins.swc.rs/versions/from-plugin-runner/3.0.0 for the list of the compatible versions.

                       Build info:
                           Date: 2024-11-04
                           Timestamp: 2024-11-04T01:54:05.821856000Z

                       Version info:
                           swc_plugin_runner: 3.0.0
                           Dependencies: anyhow 1.0.92,codspeed-criterion-compat 2.7.2,criterion 0.5.1,enumset 1.1.5,futures 0.3.31,once_cell 1.20.2,parking_lot 0.12.3,serde 1.0.214,serde_json 1.0.132,swc_atoms 2.0.0,swc_common 3.0.0,swc_css_ast 3.0.0,swc_css_parser 3.0.0,swc_ecma_ast 3.0.0,swc_ecma_loader 3.0.0,swc_ecma_parser 4.0.0,swc_ecma_visit 3.0.0,swc_malloc 1.0.0,swc_plugin_proxy 3.0.0,testing 3.0.0,tokio 1.41.0,tracing 0.1.40,vergen 9.0.1,virtual-fs 0.16.0,wasmer 4.3.7,wasmer-cache 4.3.7,wasmer-compiler-cranelift 4.3.7,wasmer-wasix 0.27.0

    2: RuntimeError: unreachable
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
failed to handle: failed to invoke plugin: failed to invoke plugin on 'Some("index.js")'

Caused by:
    0: failed to invoke `@swc/plugin-styled-components` as js transform plugin at @swc/plugin-styled-components
    1: failed to run Wasm plugin transform. Please ensure the version of `swc_core` used by the plugin is compatible with the host runtime. See the documentation for compatibility information. If you are an author of the plugin, please update `swc_core` to the compatible version.

                       Note that if you want to use the os features like filesystem, you need to use `wasi`. Wasm itself does not have concept of filesystem.

                       https://swc.rs/docs/plugin/selecting-swc-core

                       See https://plugins.swc.rs/versions/from-plugin-runner/3.0.0 for the list of the compatible versions.

                       Build info:
                           Date: 2024-11-04
                           Timestamp: 2024-11-04T01:54:05.821856000Z

                       Version info:
                           swc_plugin_runner: 3.0.0
                           Dependencies: anyhow 1.0.92,codspeed-criterion-compat 2.7.2,criterion 0.5.1,enumset 1.1.5,futures 0.3.31,once_cell 1.20.2,parking_lot 0.12.3,serde 1.0.214,serde_json 1.0.132,swc_atoms 2.0.0,swc_common 3.0.0,swc_css_ast 3.0.0,swc_css_parser 3.0.0,swc_ecma_ast 3.0.0,swc_ecma_loader 3.0.0,swc_ecma_parser 4.0.0,swc_ecma_visit 3.0.0,swc_malloc 1.0.0,swc_plugin_proxy 3.0.0,testing 3.0.0,tokio 1.41.0,tracing 0.1.40,vergen 9.0.1,virtual-fs 0.16.0,wasmer 4.3.7,wasmer-cache 4.3.7,wasmer-compiler-cranelift 4.3.7,wasmer-wasix 0.27.0

    2: RuntimeError: unreachable
Error: Failed to compile 1 file with swc.
    at Object.assertCompilationResult (/Users/fotis/swc-1.8.0-and-plugin-styled-components-4.0.0/node_modules/.pnpm/@swc+cli@0.5.0_@swc+core@1.8.0/node_modules/@swc/cli/lib/swc/util.js:165:15)
    at files (/Users/fotis/swc-1.8.0-and-plugin-styled-components-4.0.0/node_modules/.pnpm/@swc+cli@0.5.0_@swc+core@1.8.0/node_modules/@swc/cli/lib/swc/file.js:205:19)
    at async _default (/Users/fotis/swc-1.8.0-and-plugin-styled-components-4.0.0/node_modules/.pnpm/@swc+cli@0.5.0_@swc+core@1.8.0/node_modules/@swc/cli/lib/swc/file.js:224:9)
```
