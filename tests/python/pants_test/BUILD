# Copyright 2014 Pants project contributors (see CONTRIBUTORS.md).
# Licensed under the Apache License, Version 2.0 (see LICENSE).

python_library(
  name='test_infra',
  dependencies=[
    'tests/python/pants_test:base_test',
    'tests/python/pants_test:int-test-for-export',
    'tests/python/pants_test/jvm:jar_task_test_base',
    'tests/python/pants_test/jvm:nailgun_task_test_base',
    'tests/python/pants_test/jvm:jvm_tool_task_test_base',
    'tests/python/pants_test/engine:engine_test_base',
    'tests/python/pants_test/subsystem:subsystem_utils',
  ],
  provides=pants_setup_py(
    name='pantsbuild.pants.testinfra',
    description='Test support for writing pants plugins.',
    namespace_packages=['pants_test'],
    additional_classifiers=[
      'Topic :: Software Development :: Testing',
    ]
  )
)

python_library(
  name = 'base_test',
  sources = ['base_test.py'],
  dependencies = [
    'src/python/pants/base:build_file',
    'src/python/pants/base:build_root',
    'src/python/pants/base:cmd_line_spec_parser',
    'src/python/pants/base:exceptions',
    'src/python/pants/base:project_tree',
    'src/python/pants/build_graph',
    'src/python/pants/init',
    'src/python/pants/source',
    'src/python/pants/subsystem',
    'src/python/pants/task',
    'src/python/pants/util:dirutil',
    'tests/python/pants_test/base:context_utils',
    'tests/python/pants_test/option/util',
  ]
)

python_library(
  name = 'int-test-for-export',
  sources = [
    'pants_run_integration_test.py'
  ],
  dependencies = [
    '3rdparty/python:ansicolors',
    'src/python/pants/base:build_environment',
    'src/python/pants/base:build_file',
    'src/python/pants/fs',
    'src/python/pants/subsystem',
    'src/python/pants/util:contextutil',
    'src/python/pants/util:dirutil',
    'src/python/pants/util:process_handler',
    'tests/python/pants_test/testutils:file_test_util',
    'tests/python/pants_test/testutils:pexrc_util',
  ]
)

target(
  name = 'int-test',
  dependencies=[
    ':int-test-for-export',
    # NB: 'pants_run_integration_test.py' runs ./pants in a subprocess, so test results will depend
    # on the pants binary and all of its transitive dependencies. Adding this dependency is our best
    # proxy for ensuring that any test target depending on this target will be invalidated on
    # changes to those undeclared dependencies. Note that this concern is not applicable in CI due
    # to the use of clean-all.
    # There may be a better way to do this.
    'src/python/pants/bin:pants_local_binary',
  ],
)

python_tests(
  name = 'test_maven_layout',
  sources = ['test_maven_layout.py'],
  dependencies = [
    ':base_test',
    'src/python/pants/backend/jvm/subsystems:junit',
    'src/python/pants/build_graph',
    'src/python/pants/source',
    'tests/python/pants_test/subsystem:subsystem_utils',
  ]
)
