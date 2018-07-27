project('toml', 'd',
    meson_version: '>=0.46',
    license: 'MIT',
    version: '1.0.0'
)

project_soversion    = '0'

src_dir = include_directories('src/')
json_src_dir = include_directories('json/src/')
pkgc = import('pkgconfig')

toml_src = [
    'src/toml/toml.d',
    'src/toml/package.d',
    'src/toml/datetime.d',
    'json/src/toml/json.d'
]
install_headers(toml_src, subdir: 'd/toml-d/toml/')

toml_lib = library('toml-d',
        [toml_src],
        include_directories: [src_dir, json_src_dir],
        install: true,
        version: meson.project_version(),
        soversion: project_soversion
)

pkgc.generate(name: 'toml-d',
              libraries: toml_lib,
              subdirs: 'd/toml-d/',
              version: meson.project_version(),
              description: 'D implementation of Tom Obvious Minimal Language (TOML)'
)

# for use by others which embed this as subproject
toml_dep = declare_dependency(
    link_with: [toml_lib],
    include_directories: [src_dir, json_src_dir]
)
