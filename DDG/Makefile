CC = clang
CCPLUS=clang++
CFLAGS=-emit-llvm -S
FILE=main
FOLDER=tests/path

all: instrument sdg

clean: 
	rm -f $(FOLDER)/*.bc $(FOLDER)/*.ll $(FOLDER)/*.dot $(FOLDER)/*.s $(FOLDER)/*_instr $(FOLDER)/*.stats

instrument: 
	opt -load /home/su/DDG-master/DDG/build/libLLVMDDG.so -DDG $(FOLDER)/$(FILE).bc -o $(FOLDER)/$(FILE)_instr.bc
	llc -o $(FOLDER)/$(FILE)_instr.s $(FOLDER)/$(FILE)_instr.bc
	$(CCPLUS) $(FOLDER)/$(FILE)_instr.s -o $(FOLDER)/$(FILE)_instr -L /home/su/DDG-master/DDG/DDG_runtime -lmy_lib

sdg: 
	/home/su/dg/build/tools/llvm-dg-dump $(FOLDER)/$(FILE).bc > $(FOLDER)/$(FILE).dot

ddg: $(FOLDER)/$(FILE).dot tests/path/main.stats ddg.py
	python3 ddg.py -graph $(FOLDER)/$(FILE).dot -dynamic tests/path/main.stats -save $(FOLDER)/$(FILE)_new.dot
