## 动态依赖图的构造

### 1.环境配置

首先确保您的计算机中安装了以下环境：
	
	python 2.7+
	LLVM 4.5+
	cmake
我的环境配置：

	python 3.5
	LLVM 6.0.1

### 2.LLVM

将DDG文件夹拷贝到您的计算机中，执行以下命令：
	
	cd DDG

	mkdir build && cd build
        	
	cmake..

	make
        
执行完以上命令后，将DDG_runtime文件夹中的libmy_lib.so添加到LD_LIBRARY_PATH中，如：
		
	export LD_LIBRARY_PATH=/home/su/DDG-master/DDG/DDG_runtime



### 3.运行测试用例

修改Makefile中文件夹名称及路径，执行以下命令：

	make

此时会生成程序的可执行文件，执行该文件，将`2048 10 2`替换为您程序的输入：

	./main_instr 2048 10 2

	make ddg


	
