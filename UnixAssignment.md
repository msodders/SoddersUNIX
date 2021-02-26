UNIX ASSIGNMENT Maggie Sodders 

Data Inspection

Attributes of fang_et_al_genotypes

	Mkdir inspection
	awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt  | cat > fangCOL
	mv fangCOL inspection/
	du -h fang_et_al_genotypes.txt  | cat > fangFILES
	mv fangFILES inspection/
	file fang_et_al_genotypes.txt 
By inspecting this file I learned that:
1. The number of columns in this files is 986. 
2. Using column commands it is easy to see
3. Sample Id is the first column name 
4. Group is column 3 
5. The file size for this file is 6.1M
6. This file has 2783 lines with 11051939 characters 
7. This file has all characters in ASCII 

Attributes of snp_position.txt

	awk -F "\t" '{print NF; exit}' snp_position.txt  | cat > snpCOL
	du -h snp_position.txt | cat > snpFILES
	wc snp_position.txt  | cat > snpWC
	mv snpCOL inspection/ 
	mv snpFILES inspection/
	mv snpWC inspection/
	file snp_position.txt
By inspecting this file I learned that:
1. The number of columns in this files is 15. 
2. Using column commands it is easy to see
3. SNP Id is the first column name 
4. The chromosome is column 3 
5. The position is column 4 
6. The file size for this file is 38K
7. This file has 984 lines with 82763 characters 
8. This file has all characters in ASCII
