.PHONY: download all clean

all:
	(cd spdk && ./configure && make -j8)
	make -C nvml -j8

#shouldn't redownload DPDK, there is an issue right now with fPIC; it's manually
#added in its Makefile (mk/rte.lib.mk, line 53 has CFLAGS += -fPIC).
#DPDK has a config to make it shared (CONFIG_RTE_BUILD_SHARED_LIB=y)
#but it breaks SPDK compilation
redownload:
	########
	# 	NVML
	########
	@rm -rf nvml
	git clone https://github.com/pmem/nvml

clean:
	make clean -C spdk
	make clean -C nvml
