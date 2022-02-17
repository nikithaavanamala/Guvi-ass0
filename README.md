# Guvi-ass0

#Registration and Login system with Python, file handling

import re

#password validation

def check_pass(passwd):
	
	reg = "^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!#%*?&]{6,20}$"

	pat = re.compile(reg)
				
	mat = re.search(pat, passwd)

	if mat:
		return "valid"
	else:
		print("Re-enter a new password.")
    
#email validation

def check_userid(email):

   regex = re.compile(r'([A-Za-z0-9]+[.-_])*[A-Za-z0-9]+@[A-Za-z0-9-]+(\.[A-Z|a-z]{2,})+')
   
   if(re.fullmatch(regex, email)):
   
      return "valid"
   else:
      
      print("Invalid Email")

#start of main function program

def choose():

   choise = int(input("Press 1 for Signup \nPress 2 for Signin")
   
   if choise == 1:
   
      return register()
      
   elif choise == 2:
      
      return Signing_In()
   
   else:
   
      return "\nPlease re-enter your choise correctly"

#For Sign UP

def register():

   print("\nEnter the following details: ")
   
   name = input("\nName: ")
   email = input("\nUser ID: ")
   pwd = input("\nPassword: ")
   
   if(check_userid(email) == "valid" and check_pass(pwd) == "valid"):
   
      file = open("User_Data.txt",'r')
      info = file.read()
      
      if name in info:
         return "Name Unavailable. Please Try Again"
      file.close()
      
      file = open("User_Data.txt",'w')
      info = name + " " + email + " " + pwd
      file.write(info)
      
      return "Registration Successful" 
   

#For Sign In

def Signing_In():
   
   print("\nEnter the following details: ")
   
   name = input("\nName: ")
   email = input("\nUser ID: ")
   pwd = input("\nPassword: ")
   
   file = open("User_Data.txt",'r')
   info = file.read()
   info = info.split()
   
   if name in info:
   
      index = info.index(name) + 1
      usr_password = info[index]
      
      if usr_password == pwd:
      
         return "Welcome Back, " + name
      else:
      
         return "Password entered is wrong"
   else:
   
      return "New User. Please Sign Up."
   
   
print(choose())
