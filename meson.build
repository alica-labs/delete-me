project('delete_me', 'cpp',
  version : '0.0.0',
  meson_version: '>=0.56.0',
  license : 'MPL-2.0')

project_description = 'A library that defines the solver interface of the ALICA Framework.'

alica_common_config = dependency('alica_common_config', fallback : ['alica_common_config'])


project_headers = [
  'include/alica_solver_interface/Interval.h',
  'include/alica_solver_interface/SimpleContext.h',
  'include/alica_solver_interface/SolverContext.h',
  'include/alica_solver_interface/SolverTerm.h',
  'include/alica_solver_interface/SolverVariable.h'
]

project_source_files = [
  'src/SolverTerm.cpp',
  'src/SolverVariable.cpp'
]

project_test_files = [
]

build_args = [
]


# ===================================================================

# ======
# Target
# ======

public_headers = include_directories('include')

build_args += [
  '-DPROJECT_NAME=' + meson.project_name(),
  '-DPROJECT_VERSION=' + meson.project_version(),
]

project_target = library(
  meson.project_name(),
  project_source_files,
  c_args : build_args,
  include_directories : public_headers,
  dependencies : alica_common_config
)


# =======
# Project
# =======

# Make this library usable as a Meson subproject.
project_dep = declare_dependency(
  include_directories: public_headers,
  link_with : project_target,
  version : meson.project_version(),
)
meson.override_dependency(meson.project_name(), project_dep)
