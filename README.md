# FlashCPLD V2
---
## Version
TV0.1
---
## Description
via FlashTool Cycle FLash CPLD
---
## 使用环境
	python3
---
##使用放法
	1. 修改config.yaml 配置文件
		product: nidoking
		# for ac cycle
		PDU_Inlet: [1,2]
		MLB:
			- {index: 1, image: /root/Nidoking_MLB_CPLD_0x80B9_v1.5.jed, version: '15'}
			- {index: 1, image: /root/Nidoking_MLB_CPLD_0x80B9_v1.5.jed, version: '15'}
		2BP:
			- {index: 2, image: dfasaf, version: 0f}
			- {index: 2, image: dfasaf, version: 0f}
		12BP:
			- {index: 3, image: dfasaf, version: 0f}
			- {index: 3, image: dfasaf, version: 0f}


	2. usage: flashcpld.py [-h] [-p {ac,dc}] [-l LOOPS]
                    [-d {MLB,2BP,12BP} [{MLB,2BP,12BP} ...]] [--ignore]
                    [-H IP] [-U USERNAME] [-P PASSWORD]

		CPLD firmware Upgrade and downgrade

		optional arguments:
		  -h, --help            show this help message and exit
		  -p {ac,dc}, --power_mode {ac,dc}
								Set power cycle mode
		  -l LOOPS, --loops LOOPS
								Set flash cycle times(default:1)
		  -d {MLB,2BP,12BP} [{MLB,2BP,12BP} ...], --device {MLB,2BP,12BP} [{MLB,2BP,12BP} ...]
								Set flash device(default:['MLB'])

		Ignore error, continue program:
		  --ignore              Ignore error

		for out band flash:
		  -H IP                 BMC ip address
		  -U USERNAME           BMC user name
		  -P PASSWORD           BMC user password
---	  
## 结果检查
	reports/
	├── CPLD_Flash-log      		  程序输出日志
	├── flash.log           		  刷新日志
	├── logscompare_error.log         cyclelogs比较fail结果
	├── summary.log					
	└── version_compare.log           版本比较日志

	cyclelogs/
	├── fru_full.log
	├── fru_log
	│?? ├── fru.log.1
	│?? └── fru.log.2
	├── sdr_full.log
	├── sdr_log
	│?? ├── sdr.log.1
	│?? └── sdr.log.2
	├── sel_full.log
	└── sel_log
	│?? ├── sel.log.1
	│??	└── sel.log.2
	|	├── logs                            带内刷新比较日志（log.1 第一次生成的log， 做为比较模板）
	│?? ├── cpu_cores.log.1
	│?? ├── cpu_procs.log.1
	│?? ├── cpu_speed.log.1
	│?? ├── disks.log.1
	│?? ├── dmidecode_type_0.log.1
	│?? ├── dmidecode_type_1.log.1
	│?? ├── dmidecode_type_2.log.1
	│?? ├── dmidecode_type_3.log.1
	│?? ├── ipmi_bmc.log.1
	│?? ├── ipmi_lan.log.1
	│?? ├── ipmi_power_restore_police.log.1
	│?? ├── ipmi_restart_cause.log.1
	│?? ├── ipmi_sol.log.1
	│?? ├── lspcivvv.log.1
	│?? ├── lspcivvv.log.2
	│?? ├── memory.log.1
	│?? ├── pci.log.1
	│?? └── total_memory.log.1
