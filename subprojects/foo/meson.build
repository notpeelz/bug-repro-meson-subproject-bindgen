project(
  'foo',
  'rust',
  version: '1.0.0',
  default_options: [
    'rust_std=2021',
  ],
)

rust = import('unstable-rust')

obs_dep = dependency('libobs')

generated = rust.bindgen(
  input: 'foo.h',
  output: 'generated.rs',
  args: [
    '--blocklist-item', 'FE_TONEAREST',
    '--blocklist-item', 'FE_TOWARDZERO',
    '--blocklist-item', 'FE_UPWARD',
    '--blocklist-item', 'FE_DOWNWARD',
    '--blocklist-item', 'FE_INEXACT',
    '--blocklist-item', 'FE_UNDERFLOW',
    '--blocklist-item', 'FE_OVERFLOW',
    '--blocklist-item', 'FE_DIVBYZERO',
    '--blocklist-item', 'FE_INVALID',
    '--blocklist-item', 'FP_NORMAL',
    '--blocklist-item', 'FP_SUBNORMAL',
    '--blocklist-item', 'FP_ZERO',
    '--blocklist-item', 'FP_INFINITE',
    '--blocklist-item', 'FP_NAN',
  ],
  dependencies: [obs_dep],
)

foo_lib = static_library(
  'foo',
  structured_sources([
    'src/lib.rs',
    generated,
  ]),
  rust_abi: 'rust',
  # rust_crate_type: 'rlib',
  dependencies: [obs_dep],
)
