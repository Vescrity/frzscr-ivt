project(
    'frzscr', 'c',
    version: '1.0.0',
    license: 'GPL-3.0-or-later',
    default_options: ['warning_level=3']
)

add_project_arguments('-Wno-gnu-zero-variadic-macro-arguments', language: 'c')
add_project_arguments('-Wno-unused-parameter', language: 'c')
add_project_arguments('-Wno-unused-variable', language: 'c')

wayland_scanner = find_program('wayland-scanner')
wayland_client_dep = dependency('wayland-client')
omp_dep = dependency('openmp', required: false)

subdir('protocols')

executable('frzscr',
    'src/frzscr.c',
    'src/wayland.c',
    'src/overlay.c',
    'src/shm.c',
    'src/screenshot.c',
    'src/utils.c',
    'src/config.c',
    'src/xmalloc.c',
    protocol_sources,
    dependencies: [wayland_client_dep, omp_dep],
    install: true
)

install_data(
  'frzscr.1',
  install_dir: join_paths(get_option('mandir'), 'man1'),
)

