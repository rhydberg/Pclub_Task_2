Approach:

First i gained access to the file using chmod u+x
Then I ran basic analysis by running strings rev and found the strings used in the code.

Then i tried using objdump to read the dissassembly.
However that did not go so well, so i tried using radare2. That clarified the function calls more but I wasnt able to decipher everything

Then i used Ghidra to decompile the binary.

main:

There was an character array of size 31. This is where the input was getting stored. The last character is for null so the password must be 30 characters long.
Then the program outputted: 
WELCOME!
Made by: Shivam Mishra
Setting up the challenge........
Please enter the password.

then, if there is some error in taking the password, then "ERROR: Password not recognized" is printed.
otherwise checkPassword is called on the array that input was taken in.
if checkPassword returns 1 then "Access Granted!"
else "ERROR: Invalid Password"

in checkPassword,
checkPassword is a bool function, which takes a pointer.
then there are 30 local variables which store 5 3 6 5 2 5 3 3 3 5 2 4 6 5 5 2 2 5 2 6 5 1 3 4 5 3 4 6 6 5 in that order.
then process is called with the array passed to checkPassword and the address of the variable storing 5.

in process



































 
