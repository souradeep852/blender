# SPDX-FileCopyrightText: 2023 Blender Authors
#
# SPDX-License-Identifier: GPL-2.0-or-later

set(INC
  ../include
  ../../asset_system
  ../../blenkernel
  ../../blenloader
  ../../blentranslation
  ../../gpu
  ../../makesrna
  ../../windowmanager
  ../../../../intern/eigen
  # RNA_prototypes.h
  ${CMAKE_BINARY_DIR}/source/blender/makesrna
)

set(INC_SYS
)

set(SRC
  armature_add.cc
  armature_edit.cc
  armature_naming.cc
  armature_ops.cc
  armature_relations.cc
  armature_select.cc
  armature_skinning.cc
  armature_utils.cc
  bone_collections.cc
  editarmature_undo.cc
  meshlaplacian.cc
  pose_edit.cc
  pose_lib_2.cc
  pose_select.cc
  pose_slide.cc
  pose_transform.cc
  pose_utils.cc

  armature_intern.h
  meshlaplacian.h
)

set(LIB
  PRIVATE bf::animrig
  PRIVATE bf::blenfont
  bf_blenkernel
  PRIVATE bf::blenlib
  PRIVATE bf::depsgraph
  PRIVATE bf::dna
  PRIVATE bf::intern::clog
  PRIVATE bf::intern::guardedalloc
)


blender_add_lib(bf_editor_armature "${SRC}" "${INC}" "${INC_SYS}" "${LIB}")

# RNA_prototypes.h
add_dependencies(bf_editor_armature bf_rna)
