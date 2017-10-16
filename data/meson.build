
install_data(['org.gnome.BatteryBench.desktop'],
  install_dir : join_paths(get_option('datadir'), 'applications')
)


conf = configuration_data()
conf.set('LIBEXECDIR',
         join_paths(get_option('prefix'),
		    get_option('libexecdir')))
conf.set('BINDIR',
         join_paths(get_option('prefix'),
		    get_option('bindir')))

configure_file(
  input : 'org.gnome.BatteryBench.service.in',
  output : 'org.gnome.BatteryBench.service',
  configuration : conf,
  install: true,
  install_dir: join_paths(get_option('datadir'),
                          'dbus-1',
                          'services'),
)

configure_file(
  input : 'org.gnome.BatteryBench.Helper.service.in',
  output : 'org.gnome.BatteryBench.Helper.service',
  configuration : conf,
  install: true,
  install_dir: join_paths(get_option('datadir'),
                          'dbus-1',
                          'system-services'),
)

install_data(['org.gnome.BatteryBench.Helper.conf'],
  install_dir : join_paths(get_option('sysconfdir'), 'dbus-1', 'system.d')
	    )

install_data(['org.gnome.BatteryBench.Helper.policy'],
  install_dir : join_paths(get_option('datadir'), 'polkit-1', 'actions')
)
