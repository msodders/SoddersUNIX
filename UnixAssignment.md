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

cut -f3 fang_et_al_genotypes.txt | sort | uniq -c

sorts the genotypes, an counts the number of unique words in the fang et al file given 

	grep 'ZMM' fang_et_al_genotypes.txt > maize_genotypes.txt

All maize start with ZMM so this ids them and puts those rows a new file 

	grep 'ZMP' fang_et_al_genotypes.txt > teosinte_genotypes.txt
All teosinte start with ZMP so this ids them and puts those rows a new file 

	head -n 1 fang_et_al_genotypes.txt > header.txt
header row into its own file 

	cat header.txt maize_genotypes.txt > header_maize_genotypes.txt
adds header to maize file 

	awk -f transpose.awk header_maize_genotypes.txt > transposed_maize_genotypes.txt
tranposes maize 

	cat header.txt teosinte_genotypes.txt > header_teosinte_genotypes.txt
adds header to teosinte file

	awk -f transpose.awk header_teosinte_genotypes.txt > transposed_teosinte_genotypes.txt

transposes teosinte

	tail -n +2 snp_position.txt | sort -k1,1 > sorted_snp_position.txt
sorts new file no  header

	head -n 1 snp_position.txt > snp_header.txt
	tail -n +2 transposed_maize_genotypes.txt | sort -k1,1 > sorted_transposed_maize_genotypes.txt
sorted_snp position file 

	tail -n +2 transposed_teosinte_genotypes.txt | sort -k1,1 > sorted_transposed_teosinte_genotypes.txt ###Join Sorted Files
	join -t $'\t' -1 1 -2 1 sorted_snp_position.txt sorted_transposed_maize_genotypes.txt > joined_maize_genotypes.txt
sorted the transposed maize file 
join maize file 

	cut -f1,3,4,16-1586 joined_maize_genotypes.txt > pared_joined_maize_genotypes.txt
keeps only desired columns maize file


	join -t $'\t' -1 1 -2 1 sorted_snp_position.txt sorted_transposed_teosinte_genotypes.txt > joined_teosinte_genotypes.txt
sorted the transposed teosinte file 
join teosinte file 


	cut -f1,3,4,16-988 joined_teosinte_genotypes.txt > pared_joined_teosinte_genotypes.txt
keeps only desired columns teosinte file


	awk '$2 == 1' pared_joined_maize_genotypes.txt | sort -k3,3n > c1_increasing_maize.txt
	awk '$2 == 2' pared_joined_maize_genotypes.txt | sort -k3,3n > c2_increasing_maize.txt
	awk '$2 == 3' pared_joined_maize_genotypes.txt | sort -k3,3n > c3_increasing_maize.txt
	awk '$2 == 4' pared_joined_maize_genotypes.txt | sort -k3,3n > c4_increasing_maize.txt
	awk '$2 == 5' pared_joined_maize_genotypes.txt | sort -k3,3n > c5_increasing_maize.txt
	awk '$2 == 6' pared_joined_maize_genotypes.txt | sort -k3,3n > c6_increasing_maize.txt
	awk '$2 == 7' pared_joined_maize_genotypes.txt | sort -k3,3n > c7_increasing_maize.txt
	awk '$2 == 8' pared_joined_maize_genotypes.txt | sort -k3,3n > c8_increasing_maize.txt
	awk '$2 == 9' pared_joined_maize_genotypes.txt | sort -k3,3n > c9_increasing_maize.txt
	awk '$2 == 10' pared_joined_maize_genotypes.txt | sort -k3,3n > c10_increasing_maize.txt
Makes files for each chromosome increasing maize 


	sed -e 's/?/-/g' pared_joined_maize_genotypes.txt > maize_genotypes_unknowns_dashes.txt
	sed -e 's/?/?/g' pared_joined_maize_genotypes.txt > maize_genotypes_unknowns_dashes.txt
	awk '$2 == 1' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr1_decreasing_SNPs_maize.txt
	awk '$2 == 2' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr2_decreasing_SNPs_maize.txt
	awk '$2 == 3' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr3_decreasing_SNPs_maize.txt
	awk '$2 == 4' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr4_decreasing_SNPs_maize.txt
	awk '$2 == 5' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr5_decreasing_SNPs_maize.txt
	awk '$2 == 6' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr6_decreasing_SNPs_maize.txt
	awk '$2 == 7' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr7_decreasing_SNPs_maize.txt
	awk '$2 == 8' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr8_decreasing_SNPs_maize.txt
	awk '$2 == 9' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr9_decreasing_SNPs_maize.txt
	awk '$2 == 10' maize_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr10_decreasing_SNPs_maize.txt
Make files for each chromosome decreasing maize 
Make unknown - 
Make unknown ? 


	awk '$2 == 1' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr1_increasing_SNPs_teosinte.txt
	awk '$2 == 2' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr2_increasing_SNPs_teosinte.txt
	awk '$2 == 3' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr3_increasing_SNPs_teosinte.txt
	awk '$2 == 4' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr4_increasing_SNPs_teosinte.txt
	awk '$2 == 5' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr5_increasing_SNPs_teosinte.txt
	awk '$2 == 6' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr6_increasing_SNPs_teosinte.txt
	awk '$2 == 7' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr7_increasing_SNPs_teosinte.txt
	awk '$2 == 8' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr8_increasing_SNPs_teosinte.txt
	awk '$2 == 9' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr9_increasing_SNPs_teosinte.txt
	awk '$2 == 10' pared_joined_teosinte_genotypes.txt | sort -k3,3n > chr10_increasing_SNPs_teosinte.txt
Make files for each chromosome increasing teosinte 

	sed -e 's/?/-/g' pared_joined_teosinte_genotypes.txt > teosinte_genotypes_unknowns_dashes.txt
	sed -e 's/?/?/g' pared_joined_teosinte_genotypes.txt > teosinte_genotypes_unknowns_dashes.txt
	awk '$2 == 1' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr1_decreasing_SNPs_teosinte.txt
	awk '$2 == 2' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr2_decreasing_SNPs_teosinte.txt
	awk '$2 == 3' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr3_decreasing_SNPs_teosinte.txt
	awk '$2 == 4' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr4_decreasing_SNPs_teosinte.txt
	awk '$2 == 5' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr5_decreasing_SNPs_teosinte.txt
	awk '$2 == 6' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr6_decreasing_SNPs_teosinte.txt
	awk '$2 == 7' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr7_decreasing_SNPs_teosinte.txt
	awk '$2 == 8' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr8_decreasing_SNPs_teosinte.txt
	awk '$2 == 9' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr9_decreasing_SNPs_teosinte.txt
	awk '$2 == 10' teosinte_genotypes_unknowns_dashes.txt | sort -k3,3nr > chr10_decreasing_SNPs_teosinte.txt

Make files for each chromosome decreasing teosinte 
Make unknown - 
Make unkown ? 



Maize and Teosinte Both mixes but all code and what they tell me should be listed underneath code. 