project(
  'blah',
  'rust',
  version: '1.0.0',
  default_options: [
    'rust_std=2021',
  ],
)

rust = import('unstable-rust')
foo = subproject('foo')
foo_lib = foo.get_variable('foo_lib')

shared_library(
  'blah',
  structured_sources([
    'src/lib.rs',
  ]),
  rust_abi: 'c',
  # rust_crate_type: 'cdylib',
  link_with: [
    foo_lib,
  ],
  name_prefix: '',
)
