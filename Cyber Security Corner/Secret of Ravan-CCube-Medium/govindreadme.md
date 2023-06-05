```
import pyzipper  
characters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '!', '@', '#', '$', '%', '^', '&', '*', '(', ')', '_', '-', '+', '=', '{', '}', '[', ']', '|', ';', ':', '"', "'", '<', '>', '?', ',', '.', '/', '`', '~']
known_password_dict = {'n':1, '_':2, '^':3, '`':5, 'W':6, '5':8}
zip_file_path=r"C:\Users\govin\Music\The_secret.zip"  #location of the target file ,which is The_secret.zip
extract_to_dir=r"C:\Users\govin\Music\trial"          #location to which the file is to be extracted
list = ['n',"_",'','^','`','W','','5']                #password character list
for i in characters:                                  #first for loop to loop through chracters in the third index

    list[3]=i
    
    for j in characters:                              #second nested for loops for looping though characters in the 6th index
        list[6]=j 
        paswrd=''.join(list)                           #to make the list into a string
        print(paswrd)
        
        try:
            with pyzipper.ZipFile(zip_file_path) as zf:   #using pyzipper to try the password
                zf.extractall(path=extract_to_dir,pwd=paswrd.encode)
        except:
            continue
```

`import pyzipper`-to import the pyzipper modile

We do not know what the characters are in the third and sixth index, so we use brute forcing to try every possible combination.To do that we use nested loops.Then using pyzipper
in a try except codewe save the file to another location.

```
for i in characters:
    list[3]=i
 ```
 This is the outer for loop.This is used to try every character in the third position.
```
for j in characters:                              
        list[6]=j 
 ```
 This is the inner for loop.This is used to try every character in the sixth position.
```
paswrd=''.join(list)                           
        print(paswrd)
```
 Joins the list into a string
 ```
 try:
            with pyzipper.ZipFile(zip_file_path) as zf:   #using pyzipper to try the password
                zf.extractall(path=extract_to_dir,pwd=paswrd.encode)
        except:
            continue
  ```
  Since we need to try each possibility from the loop, we use a try except code.Otherwise, if the first code is wrong
  it will result in an error and the code will stop.In the brackets of the pyzipper.ZipFile command, we give the path or location of the zipfile.
  In the zf.extractall command ,we give the path of the directory to which the file is to be saved is given.we give the password as the second argument after converting it
  into byte format using encode command.In the except , we give continue so that the code continues if the password is wrong.
 
 
    
