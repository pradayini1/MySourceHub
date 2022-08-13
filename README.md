22

#!/bin/sh
# shebang to specify that this is an shell script

# Function to get File
getFile(){
    # Reading txtFileName to convert it's content
    echo -n "Enter File Name:"
    read txtFileName
    # Checking if file exist
    if [ ! -f $txtFileName ]; then
        echo "File Name $txtFileName does not exists."
        exit 1
    fi
}

clear
  echo "1. Uppercase to Lowercase "
  echo "2. Lowercase to Uppercase"
  echo "3. Exit"
  echo -n "Enter your Choice(1-3):"
  read Ch

  case "$Ch" in
    1) 
      # Function Call to get File 
      getFile    
      # Converting to lower case if user chose 1     
      echo "Converting Upper-case to Lower-Case "
      tr '[A-Z]' '[a-z]' <$txtFileName
    ;;

    2)
      # Function Call to get File 
      getFile
      # Converting to upper case if user chose 2
      echo "Converting Lower-Case to Upper-Case "
      tr '[a-z]' '[A-Z]' <$txtFileName
    ;;
    

    *) # exiting for all other cases
        echo "Exiting..."
        exit
    ;;
  esac
-------------------------------------------------------------------------------------------
32

#!/bin/bash
usrid=(`cut -d ":" -f3 /etc/passwd`)  
if [ $# -gt 0 ]  
then
if [ $# -eq 1 ] 
then
echo "Error : Please pass 2 arguments through CL.
Usage : ./30_user_ids.sh 100 200"
elif [ $1 -gt $2 ]    
then
echo "Error : Invalid range. Please enter the valid range through CL."
else
count=0  
for i in ${usrid[@]}  
	do
if [ $i -ge $1 -a $i -le $2 ]   
	then
  let count=$count+1
	fi
	done
	echo "Total count of user ID between $1 to $2 is : $count"
	fi
     else  
   count=0
  for i in ${usrid[@]}
	do
if [ $i -ge 500 -a $i -le 10000 ]
	then
	let count=$count+1
	fi
	done
	echo "Total count of user ID between 500 to 10000 is: $count"
         fi
------------------------------------------------------------------------------------------------------------------
31

#!/bin/bash

filesys=(`df | tr -s " " | cut -d " " -f1`)
for j in ${filesys[@]}
do
        echo "$j"
done
useper=(`df | tr -s " " | cut -d " " -f5 | cut -d "%" -f1`)
for i in `seq $((${#useper[@]}-1))`
do
        if [ ${useper[i]} -ge 90 ]
        then
echo "Filesystem ${filesys[i]} have less than 10% free space"
fi
done

-----------------------------------------------------------------------------------------------------------
24

if [ $# -eq 1 ]  
then
	if [ -d $1 ]  
	then
		swps=(`find $1 -name "*.swp" -type f`)  
		if [ ${#swps[@]} -ne 0 ]  
		then
			find $1 -name "*.swp" -type f -delete   
		else
			echo "No swp files found in test_swp."
		fi
	else
		echo "Error : '$1' no such a file or directory"
	fi
else
	swps=(`find ~ -name "*.swp" -type f`)  
	if [ ${#swps[@]} -ne 0 ]  
	then
		echo "swap file found :"
		find ~ -name "*.swp" -type f  
	fi
fi
----------------------------------------------------------------2

v_num=1
v_rows=5
for((i=1; i<=$v_rows; i++))
do
  for((j=1; j<=$i; j++))
  do
    echo -n "$v_num "
    v_num=$((v_num + 1))
  done
  v_num=1
  echo
done

------------------------------------------------3
v_num=1
v_rows=4
for((i=1; i<=$v_rows; i++))
do
  for((j=1; j<=$i; j++))
  do
    echo -n "$v_num "
    v_num=$((v_num + 1))
  done
  echo
done

--------------------------------------------------------20
//Shell script to display all the 
//given lines of a file

//take file name from user
//and store the input in f variable
echo "Enter the file name :"
read f

//take starting line from user 
//and store the input in s variable
echo "Enter the starting line :"
read s 

//take endinging line from user 
//and store the input in e variable
echo "Enter the ending line :"
read e

//printing the specified lines to console.
sed -n $s,$e\p $f
------------------------------------------------23

-------------------------------------------------------23
$ cut -f 1 state.txt
Andhra Pradesh
Arunachal Pradesh
Assam
Bihar
Chhattisgarh
If -d option is used then it considered space as a field separator or delimiter:

$ cut -d " " -f 1 state.txt
Andhra
Arunachal
Assam
Bihar
Chhattisgarh

In this, -3 indicate from 1st byte to 3rd byte of a line
$ cut -b -3 state.txt
And
Aru
Ass
Bih
Chh
-------------------------------------------------------------25
randpw(){ < /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c${1:-16};echo;}
