# Copyright 2014 Pants project contributors (see CONTRIBUTORS.md).
# Licensed under the Apache License, Version 2.0 (see LICENSE).

python_library(
  name = 'plugin',
  sources = ['__init__.py', 'register.py'],
  dependencies = [
    ':pants_requirement',
    ':python_artifact',
    ':python_requirement',
    ':python_requirements',
    'src/python/pants/backend/python/targets:python',
    'src/python/pants/backend/python/tasks',
    'src/python/pants/backend/python/tasks2',
    'src/python/pants/build_graph',
    'src/python/pants/goal:task_registrar',
  ]
)

python_library(
  name = 'all_utils',
  sources = globs('*.py', exclude=[['__init__.py', 'register.py']]),
  dependencies = [
    ':antlr_builder',
    ':code_generator',
    ':interpreter_cache',
    ':python_artifact',
    ':python_chroot',
    ':python_requirement',
    ':python_requirements',
    ':sdist_builder',
    ':thrift_builder',
  ]
)

page(
  name = 'readme',
  source = 'README.md',
  links = [
    'src/python/pants:readme',
  ]
)

python_library(
  name = 'antlr_builder',
  sources = ['antlr_builder.py'],
  dependencies = [
    ':code_generator',
    'src/python/pants/base:build_environment',
    'src/python/pants/base:exceptions',
    'src/python/pants/ivy',
    'src/python/pants/util:dirutil',
  ]
)

python_library(
  name = 'code_generator',
  sources = ['code_generator.py'],
  dependencies = [
    ':sdist_builder',
    '3rdparty/python/twitter/commons:twitter.common.dirutil',
    'src/python/pants/util:dirutil'
  ]
)


python_library(
  name = 'interpreter_cache',
  sources = ['interpreter_cache.py'],
  dependencies = [
    '3rdparty/python:pex',
    'src/python/pants/backend/python/targets',
    'src/python/pants/base:exceptions',
    'src/python/pants/process',
    'src/python/pants/util:dirutil',
    'src/python/pants/util:memo',
  ]
)

python_library(
  name = 'pants_requirement',
  sources = ['pants_requirement.py'],
  dependencies = [
    'src/python/pants/backend/python:python_requirement',
    'src/python/pants/backend/python/targets:python',
    'src/python/pants/base:build_environment',
  ]
)


python_library(
  name = 'python_artifact',
  sources = ['python_artifact.py'],
  dependencies = [
    'src/python/pants/base:payload_field',
  ],
)

python_library(
  name = 'python_chroot',
  sources = ['python_chroot.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    '3rdparty/python:pex',
    ':antlr_builder',
    ':python_requirement',
    ':thrift_builder',
    'src/python/pants/backend/codegen/antlr/python',
    'src/python/pants/backend/codegen/thrift/python',
    'src/python/pants/backend/python/targets:python',
    'src/python/pants/base:build_environment',
    'src/python/pants/build_graph',
    'src/python/pants/invalidation',
    'src/python/pants/util:dirutil'
  ],
)

python_library(
  name = 'python_requirement',
  sources = ['python_requirement.py'],
)

python_library(
  name = 'python_requirements',
  sources = ['python_requirements.py'],
)

python_library(
  name = 'sdist_builder',
  sources = ['sdist_builder.py'],
  dependencies = [
    '3rdparty/python:pex',
  ]
)

python_library(
  name = 'thrift_builder',
  sources = ['thrift_builder.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    ':code_generator',
      # Note that this is part of a gnarly dependency chain:
      #  backend/python:thrift_builder ->
      #  src/python/pants/backend/codegen/thrift/python ->
      #  backend/python/targets:python
      # This isn't circular, but it's still bad that it crosses between backends and back again.
      # TODO: Clean this up. thrift_builder should almost certainly be in the codegen backend.
    'src/python/pants/backend/codegen/thrift/python',
    'src/python/pants/base:build_environment',
    'src/python/pants/util:dirutil',
    'src/python/pants/util:memo',
    'src/python/pants/util:process_handler',
  ]
)
