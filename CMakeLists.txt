# Copyright 2019 Mike Dev
# Distributed under the Boost Software License, Version 1.0.
# See accompanying file LICENSE_1_0.txt or copy at https://www.boost.org/LICENSE_1_0.txt

if(NOT DEFINED IDF_TARGET)

cmake_minimum_required( VERSION 3.5...3.20 )
project( boost_optional VERSION "${BOOST_SUPERPROJECT_VERSION}" LANGUAGES CXX )

add_library( boost_optional INTERFACE )
add_library( Boost::optional ALIAS boost_optional )

target_include_directories( boost_optional INTERFACE include )

target_link_libraries( boost_optional
    INTERFACE
        Boost::assert
        Boost::config
        Boost::core
        Boost::detail
        Boost::move
        Boost::predef
        Boost::static_assert
        Boost::throw_exception
        Boost::type_traits
        Boost::utility
)

else()

idf_component_register(
    INCLUDE_DIRS
        include
    REQUIRES
        boost_assert
        boost_config
        boost_core
        boost_detail
        boost_move
        boost_predef
        boost_static_assert
        boost_throw_exception
        boost_type_traits
        boost_utility
)

endif()

