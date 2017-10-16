if asciidoc.found() and xmlto.found()

  xml = configure_file(input: 'gbb.txt',
		       output: 'gbb.xml',
		       command: [asciidoc.path(),
				 '-f', 'asciidoc.conf',
				 '-d', 'manpage',
				 '-b', 'docbook',
				 '-o', '@OUTPUT@',
				 '@INPUT@'],
		       )

   configure_file(input: 'gbb.txt',
		  output: 'gbb.html',
		  command: [asciidoc.path(),
			    '-f', 'asciidoc.conf',
			    '-d', 'manpage',
			    '-o', '@OUTPUT@',
			    '@INPUT@'],
		  install: true,
		  install_dir: docdir)

  manpage = configure_file(input: 'gbb.txt',
			   output: 'gbb.1',
			   command: [xmlto.path(), 'man', '@INPUT@'],
			   install: false)

  install_man(manpage)
endif
