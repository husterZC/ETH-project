# 6 oct 2021
## done:
- [x] Generate a reqrsp slave following the LSU
- [x] Complete the signal drive tasks for LSU
- [x] create a interface "test/core_to_lsu_intf.sv"
- [x] Integrate the LSU drive task in class called "lsu_driver" in "test/core_to_lsu_test.sv"
- [x] Fix the bug: in "test/core_to_lsu_test.sv" class lsu_driver task send_lsu_request, generate a random lsu_req_t which do not depend on the parameter of lsu_driver but only depend on the default parameter of lsu_req_t.
## todo:
- [ ] implement the scorebard
