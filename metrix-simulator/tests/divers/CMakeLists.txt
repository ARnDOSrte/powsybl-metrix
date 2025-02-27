# 
# Copyright (c) 2021, RTE (http://www.rte-france.com)
# See AUTHORS.txt
# All rights reserved.
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, you can obtain one at http://mozilla.org/MPL/2.0/.
# SPDX-License-Identifier: MPL-2.0
# 

MESSAGE("General purpose tests...")

set(TEST_DIR_NAME divers)
set(TEST_DIR ${MAIN_TEST_DIR}/${TEST_DIR_NAME})
set(EXPECTED_TEST_DIR ${MAIN_TEST_DIR}_reference/${TEST_DIR_NAME})

metrix_test("encodage_utf8" 2)
metrix_test("probleme_bornes_ecart_1" 1)
metrix_test("probleme_bornes_ecart_2" 2)
metrix_test_check_only_results("contrainte_sans_action_possible_opf" 2) # no check metrix out because CI has a different result depending on test duration
if(METRIX_RUN_ALL_TESTS)
metrix_test("contraintes_sans_action_possible" 1)
endif()
metrix_test("tres_long" 2)
metrix_test("tout_fixe" 2)
metrix_test("tout_fixe_hr" 3)
metrix_test("resultats_equilibrage_et_variations_marginales" 4)
metrix_test("variations_marginales" 3)
metrix_test("variations_marginales_with_offset" 3)
metrix_test("variations_marginales_sur_parades" 3)
metrix_test("variations_marginales_several_bconstraints" 2)
metrix_test_check_only_results("temps_calcul_pne" 1) # no check metrix out because CI has an equivalent result during optimization
if(METRIX_RUN_ALL_TESTS)
metrix_test("bug_pne" 2)
metrix_test("gen_cost_sans_vm" 2)
endif()
if(METRIX_RUN_ALL_TESTS)
metrix_test("resultats_surcharges_uniquement" 10)
endif()
metrix_test_no_check("transits_sur_incidents" 1) # no output check because of random display order
metrix_test("redispatching_offset" 3)
