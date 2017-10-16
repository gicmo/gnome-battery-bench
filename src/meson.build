
base_sources = files([
  'event-log.c',
  'event-log.h',
  'evdev-player.c',
  'evdev-player.h',
  'event-player.c',
  'event-player.h',
  'introspection.c',
  'introspection.h',
  'remote-player.c',
  'remote-player.h',
  'util.c'	,
  'util.h'])


client_sources =  files([
  'battery-test.c',
  'battery-test.h',
  'event-recorder.c',
  'event-recorder.h',
  'power-monitor.c',
  'power-monitor.h',
  'power-supply.h',
  'power-supply.c',
  'system-info.h',
  'system-info.c',
  'system-state.c',
  'system-state.h',
  'test-run.c',
  'test-run.h',
  'test-runner.c',
  'test-runner.h',
  'xinput-wait.c',
  'xinput-wait.h',
  'util-sysfs.h',
  'util-sysfs.c'])

gbbapp_sources = files([
  'gui.c',
  'application.c',
  'application.h',
  'power-graphs.c',
  'power-graphs.h',
  'util-gtk.c',
  'util-gtk.h'])

resource_src = gnome.compile_resources(
  'gnome-battery-bench.gresource.c',
  'gnome-battery-bench.gresource.xml',
  source_dir : '.'
)

base_deps = [evdev, glib, giounix]
x11_deps = [x11, xi, xtst]
app_deps = [json_glib, gudev, gdk3]

helper_deps = [base_deps, polkit]
cmdapp_deps = [base_deps, x11_deps, app_deps]
gbbapp_deps = [cmdapp_deps, gtk3]

executable('gnome-battery-bench',
	   [base_sources, client_sources, gbbapp_sources, resource_src],
	   dependencies: gbbapp_deps,
	   include_directories: [
	     include_directories('..')
	   ],
	   install: true,
	   install_dir : get_option('bindir'))

executable('gbb',
	   [base_sources, client_sources, 'commandline.c'],
	   dependencies: cmdapp_deps,
	   include_directories: [
	     include_directories('..')
	   ],
	   install: true,
	   install_dir : get_option('bindir'))

executable('gnome-battery-bench-helper',
	   [base_sources, 'replay-helper.c'],
	   dependencies: helper_deps,
	   include_directories: [
	     include_directories('..')
	   ],
	   install: true,
	   install_dir : get_option('libexecdir'))

