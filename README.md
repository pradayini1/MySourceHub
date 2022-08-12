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
