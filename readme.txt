#!/bin/bash
int0=0
int1=0

echo "***********************************************************************"
echo "***************        Calculadora             ************************"
echo "***********************************************************************"
function getInput() {
#statements
 echo Ingrese dos digitos
          read FD LD
          echo "Digitos: $FD, $LD "
 int0=$FD
 int1=$LD
echo ""mark #; circle 40 50 20;""

}
function getInputMul() {
#statements
 intresult=0
 tempresult=0;
 echo Tipo de operacion $1
 echo Ingrese todos los dijitos separados por $1
          read FD
          IFS=$1 read -r -a array <<< ${FD}

   if [ "$1" = "-" ]; then
     #echo "substract initial: $intresult"

     #echo ${array[0]}
     #echo "fixing tempresult : $tempresult"
     tresult=$((${array[0]} + ${array[0]}))
     #echo "substract initialFixed: $intresult"

   else
     echo ""
   fi

   if [ "$1" = "x" ]; then
     #echo "multiply initial: $intresult"

     #echo ${array[0]}
     #echo "fixing tempresult : $tempresult"
     intresult=1
     #echo "multiply initialFixed: $intresult"

   else
     echo ""
   fi

   if [ "$1" = "/" ]; then
     #echo "divide initial: $intresult"

     #echo ${array[0]}
     #echo "fixing tempresult : $tempresult"
     intresult=$((${array[0]} * ${array[0]}))
     #echo "divide initialFixed: $intresult"

   else
     echo ""
   fi


   for i in "${array[@]}"
   do

   #echo Digito "$i"  operacion "$1"
       case "$1" in
         "+")

           #echo "here: $intresult"
           intresult=$(($intresult + $i))

         ;;
         "-")

           #echo "here: $intresult " " digito :$i"
           intresult=$(($intresult - $i))
         ;;
         "x")
           #echo "here multiply: $intresult " " digito :$i"
           intresult=$(($intresult * $i))
         ;;
         "/")
           intresult=$(($intresult / $i))
         ;;


         *)

         ;;
       esac


   done

   echo "Resultado: $intresult "

}

function displayresult() {
 #statements


               echo "Resultado:  $1 !"

}


function sum() {
#statements

             resultint=$(($1 + $2))
             displayresult $resultint

}
function sumMul() {
#statements

             resultint=$(($1 + $2))
             displayresult $resultint

}
function substract() {
#statements

             resultint=$(($1 - $2))
             displayresult $resultint

}

function multiply() {
#statements

             resultint=$(($1 * $2))
             displayresult $resultint

}

function divide() {
#statements

             resultint=$(($1 / $2))
             displayresult $resultint

}




OPTIONS="Suma SumaMultiple Resta RestaMultiple Division DivisionMultiple Multiplicar MultiplicarMultiple Salir"
   select opt in $OPTIONS; do
   if [ "$opt" = "Salir" ]; then
   echo done
   exit

   elif [ "$opt" = "Suma" ]; then
   echo Suma
   getInput
   sum $int0 $int1

   elif [ "$opt" = "SumaMultiple" ]; then
   echo Suma
   getInputMul "+"



   elif [ "$opt" = "Resta" ]; then
   echo Resta
   getInput
   substract $int0 $int1

   elif [ "$opt" = "RestaMultiple" ]; then
   echo RestaMultiple
   getInputMul "-"


   elif [ "$opt" = "Division" ]; then
   echo Division

   elif [ "$opt" = "DivisionMultiple" ]; then
   echo Division
   getInputMul "/"


   elif [ "$opt" = "Multiplicar" ]; then
   echo Multiplicar
   getInput
   multiply $int0 $int1

   elif [ "$opt" = "MultiplicarMultiple" ]; then
   echo Division
   getInputMul "x"


   else
   clear
   echo bad option
   fi
done
