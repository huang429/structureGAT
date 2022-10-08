#动态依赖图
##1.环境
python 3.5(2.7+即可)
LLVM 6.0.1(4.5+即可)
cmake

##2.配置步骤
cd DDG
mkdir build
cmake..
make
以上步骤执行成功后，将DDG_runtime中的libmy_lib.so添加到LD_LIBRARY_PATH中
export LD_LIBRARY_PATH=/home/su/DDG-master/DDG/DDG_runtime

##3.运行测试用例
修改Makefile中文件夹名称或路径
make
./main_instr 程序输入
make ddg
