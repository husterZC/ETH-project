Record 5 oct:
# add other repo to your repo
```
git submodule add https://github.com/pulp-platform/snitch.git
```

## if finding that the snitch folder is empty, please follow
```
rm -rf snitch
git add -A
git submodule add https://github.com/pulp-platform/snitch.git
``` 

# usage of bender.yml
example
```
package:
  name: axi-streams
  authors:
    - "Chi Zhang <chizhang@ethz.ch>"

dependencies:
  snitch_cluster: { path: snitch/hw/ip/snitch_cluster }
  axi_riscv_atomics: { path: snitch/hw/vendor/pulp_platform_axi_riscv_atomics }
  tech_cells_generic: { path: snitch/hw/vendor/pulp_platform_tech_cells_generic }

sources:
  <where to put your design code>
  - target: test
    files:
      <where to put your testbench>
      - test/tb_axi_streams.sv

```

# use Bender.local to set up the override of the dependencies
```
overrides:
  common_verification: { git: https://github.com/pulp-platform/common_verification.git, rev: master}
  tech_cells_generic: { path: src/snitch/hw/vendor/pulp_platform_tech_cells_generic }
  common_cells: { path: src/snitch/hw/vendor/pulp_platform_common_cells }
  axi: { path: src/snitch/hw/vendor/pulp_platform_axi }
  fpnew: { path: src/snitch/hw/vendor/pulp_platform_fpnew }
  riscv-dbg: { path: src/snitch/hw/vendor/pulp_platform_riscv_dbg }


```

# write a Mackefile to use bender
```
BENDER ?= bender
VLOG_ARGS = -svinputport=compat -timescale 1ns/1ps -suppress 2583 -suppress 13314


vsim/compile.tcl: Bender.yml
	$(BENDER) script vsim -t test -t rtl --vlog-arg="$(VLOG_ARGS)" > $@
```

here '-suppress 2583' is to ignore warning type 2538
$@ means 'vsim/compile.tcl'

# remember to remove bender.lock
```
rm -rf .bender Bender.lock
```

# the testbench should be writen in: 1. a fixture class which includes the instance of DUT, several tasks, 2. use testbench to instance such fixture

# useage of git
## git add -A -->to make changes in local git
## gst -->to check the statue
## git add .gitignore -->to make a ignore list
```
**/logs/
**/work
**/*.log
**/modelsim.ini
**/transcript
vsim/compile.tcl
**/*.wlf
.bender
Bender.lock
```