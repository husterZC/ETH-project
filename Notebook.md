# 6 oct 2021
## done:
- [x] Generate a reqrsp slave following the LSU
- [x] Complete the signal drive tasks for LSU
- [x] create a interface "src/core_to_lsu_intf.sv"
- [x] Integrate the LSU drive task in class called "lsu_driver" in "src/core_to_lsu_test.sv"
- [x] Fix the bug: in "test/core_to_lsu_test.sv" class lsu_driver task send_lsu_request, generate a random lsu_req_t which do not depend on the parameter of lsu_driver but only depend on the default parameter of lsu_req_t.

# 7 oct 2021
## done:
- [x] extend the testbech : driver->LSU->reqrsp_to_axi->axi_slave, in "test/tb_lsu_axi.sv"
- [X] make a monitor in 'core_to_lsu_test'
- [x] implement the scorebard

## discussion in tomorrow's meeting
- [x] Do I need to use the reqrsp_to_axi module? can I only change LSU to support ssr?
- [x] Cumstomrize a axi_slave? like a memory?
- [x] how to debug? how to use monitor? scorebaord

# 11 oct 2021
## todo
- [ ] the testbench ```driver->LSU->reqrsp_to_axi->axi_slave``` can only work at ```amo==AMONone```, this is quite strange, I will fix it later on
- [ ] 消除DUT所有的INTERFACE

# 20 oct 2021
## todo
- [ ] 注意Datawidth在testbench中，DW=64时，可能有bug 
