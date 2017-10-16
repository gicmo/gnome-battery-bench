project('gnome-battery-bench',
	      'c',
	      version: '3.25.1',
	      license : 'LGPL-2.1+',
	      meson_version: '>= 0.36.0',
	      default_options: ['warning_level=1',
			                    'c_std=gnu99',
			                    'buildtype=debugoptimized'])

gnome = import('gnome')
i18n = import('i18n')

# dependencies
evdev = dependency('libevdev')
glib = dependency('glib-2.0', version : '>= 2.44.0')
giounix = dependency('gio-unix-2.0')
x11 = dependency('x11')
xi = dependency('xi')
xtst = dependency('xtst')
json_glib = dependency('json-glib-1.0')
gudev = dependency('gudev-1.0')
gdk3 = dependency('gdk-3.0')
gtk3 = dependency('gtk+-3.0')
polkit = dependency('polkit-gobject-1')

asciidoc = find_program('asciidoc', required: false)
xmlto = find_program('xmlto', required: false)


# get suported warning flags
test_args = [
  '-fstack-protector-strong',
  '-Waggregate-return',
  '-Wunused',
  '-Warray-bounds',
  '-Wcast-align',
  '-Wclobbered',
  '-Wduplicated-branches',
  '-Wduplicated-cond',
  '-Wempty-body',
  '-Wformat=2',
  '-Wformat-nonliteral',
  '-Wformat-security',
  '-Wformat-signedness',
  '-Wignored-qualifiers',
  '-Wimplicit-function-declaration',
  '-Winit-self',
  '-Wlogical-op',
  '-Wmissing-declarations',
  '-Wmissing-format-attribute',
  '-Wmissing-include-dirs',
  '-Wmissing-noreturn',
  '-Wmissing-parameter-type',
  '-Wmissing-prototypes',
  '-Wnested-externs',
  '-Wno-discarded-qualifiers',
  '-Wno-missing-field-initializers',
  '-Wno-strict-aliasing',
  '-Wno-suggest-attribute=format',
  '-Wno-unused-parameter',
  '-Wnull-dereference',
  '-Wold-style-definition',
  '-Woverride-init',
  '-Wpointer-arith',
  '-Wredundant-decls',
  '-Wreturn-type',
  '-Wshadow',
  '-Wsign-compare',
  '-Wstrict-aliasing',
  '-Wstrict-prototypes',
  '-Wswitch-default',
  '-Wtype-limits',
  '-Wundef',
  '-Wuninitialized',
  '-Wunused-but-set-variable',
  '-Wunused-variable',
  '-Wwrite-strings'
]
cc = meson.get_compiler('c')
foreach arg: test_args
  if cc.has_argument(arg)
    add_project_arguments(arg, language : 'c')
  endif
endforeach

pkgdatadir = join_paths(get_option('prefix'), get_option('datadir'), 'gnome-battery-bench')

conf = configuration_data()
conf.set_quoted('VERSION', meson.project_version())
conf.set_quoted('PACKAGE_NAME', meson.project_name())
conf.set_quoted('PACKAGE_VERSION', meson.project_version())
conf.set_quoted('PKGDATADIR', pkgdatadir)
conf.set_quoted('DATADIR', join_paths(get_option('prefix'), get_option('datadir')))
conf.set_quoted('GNOME_SESSION_DIR', join_paths(get_option('prefix'), get_option('libexecdir')))

config_h = configure_file(output: 'config.h',
			                    configuration: conf)

subdir('data')
subdir('docs')
subdir('src')
subdir('tests')
