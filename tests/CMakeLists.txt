set(lfsc_test_file_list
  bool.plf
  mp_prefix.plf
  sat.plf
  smt.plf
  th_arrays.plf
  th_base.plf
  th_bv_bitblast.plf
  th_bv.plf
  th_int.plf
  use-bool.plf
  use-use-bool.plf
  unused_pi_param_rational_in_body.plf
  semicolon_after_id.plf
)

set(test_script ${CMAKE_CURRENT_LIST_DIR}/run_test.py)

macro(lfsc_test file)
  add_test(
    NAME ${file}
    COMMAND ${test_script} $<TARGET_FILE:lfscc> ${CMAKE_CURRENT_LIST_DIR}/tests/${file}
    WORKING_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}
  )
  set_tests_properties(${file} PROPERTIES TIMEOUT 40)
endmacro()

foreach(file ${lfsc_test_file_list})
  lfsc_test(${file})
endforeach()
