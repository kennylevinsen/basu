# SPDX-License-Identifier: LGPL-2.1+

id128_sources = files('''
        sd-id128/id128-util.c
        sd-id128/id128-util.h
        sd-id128/sd-id128.c
'''.split())

sd_daemon_c = files('sd-daemon/sd-daemon.c')
sd_event_c = files('sd-event/sd-event.c')

libsystemd_sources = files('''
        sd-bus/bus-common-errors.c
        sd-bus/bus-common-errors.h
        sd-bus/bus-container.c
        sd-bus/bus-container.h
        sd-bus/bus-control.c
        sd-bus/bus-control.h
        sd-bus/bus-convenience.c
        sd-bus/bus-creds.c
        sd-bus/bus-creds.h
        sd-bus/bus-dump.c
        sd-bus/bus-dump.h
        sd-bus/bus-error.c
        sd-bus/bus-error.h
        sd-bus/bus-gvariant.c
        sd-bus/bus-gvariant.h
        sd-bus/bus-internal.c
        sd-bus/bus-internal.h
        sd-bus/bus-introspect.c
        sd-bus/bus-introspect.h
        sd-bus/bus-kernel.c
        sd-bus/bus-kernel.h
        sd-bus/bus-match.c
        sd-bus/bus-match.h
        sd-bus/bus-message.c
        sd-bus/bus-message.h
        sd-bus/bus-objects.c
        sd-bus/bus-objects.h
        sd-bus/bus-protocol.h
        sd-bus/bus-signature.c
        sd-bus/bus-signature.h
        sd-bus/bus-slot.c
        sd-bus/bus-slot.h
        sd-bus/bus-socket.c
        sd-bus/bus-socket.h
        sd-bus/bus-track.c
        sd-bus/bus-track.h
        sd-bus/bus-type.c
        sd-bus/bus-type.h
        sd-bus/sd-bus.c
'''.split()) + id128_sources + sd_daemon_c + sd_event_c

disable_mempool_c = files('disable-mempool.c')

libsystemd_c_args = ['-fvisibility=default']

libsystemd_static = static_library(
        'systemd_static',
        libsystemd_sources,
        install : false,
        include_directories : includes,
        link_with : libbasic,
        dependencies : [threads,
                        librt],
        c_args : libsystemd_c_args)

libsystemd_sym = 'src/libsystemd/libsystemd.sym'

libsystemd_pc = configure_file(
        input : 'libbasu.pc.in',
        output : 'libbasu.pc',
        configuration : substs)
install_data(libsystemd_pc,
             install_dir : pkgconfiglibdir)
