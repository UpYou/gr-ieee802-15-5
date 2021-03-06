# Copyright 2011 Free Software Foundation, Inc.
#
# This file is part of GNU Radio
#
# GNU Radio is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3, or (at your option)
# any later version.
#
# GNU Radio is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GNU Radio; see the file COPYING.  If not, write to
# the Free Software Foundation, Inc., 51 Franklin Street,
# Boston, MA 02110-1301, USA.

########################################################################
# Setup library
########################################################################
include(GrPlatform) #define LIB_SUFFIX
include(GrPython)

add_library(gnuradio-ieee802-15-4 SHARED 
							ucla_cc1k_correlator_cb.cc 
							ucla_ieee802_15_4_packet_sink.cc 
							ucla_manchester_ff.cc 
							ucla_qpsk_modulator_cc.cc 
							ucla_symbols_to_chips_bi.cc 
							ucla_delay_cc.cc  
							ucla_multichanneladd_cc.cc 
							ucla_sos_packet_sink.cc
							)
target_link_libraries(gnuradio-ieee802-15-4 ${Boost_LIBRARIES} ${GRUEL_LIBRARIES} ${GNURADIO_CORE_LIBRARIES})
set_target_properties(gnuradio-ieee802-15-4 PROPERTIES DEFINE_SYMBOL "gnuradio_ieee802_15_4_EXPORTS")
#GR_LIBRARY_FOO(gnuradio-ieee802-15-4 RUNTIME_COMPONENT "ucla" DEVEL_COMPONENT "ucla_devel")


########################################################################
# Install built library files
########################################################################
install(TARGETS gnuradio-ieee802-15-4
    LIBRARY DESTINATION lib${LIB_SUFFIX} # .so/.dylib file
    ARCHIVE DESTINATION lib${LIB_SUFFIX} # .lib file
    RUNTIME DESTINATION bin              # .dll file
)
