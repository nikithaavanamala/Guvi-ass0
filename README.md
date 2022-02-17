# Guvi-ass0
#Registration and Login system with Python, file handling

import re

#password validation

def checkpwd(passwd):
	
	reg = "^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!#%*?&]{6,20}$"

	pat = re.compile(reg)
				
	mat = re.search(pat, passwd)

	if mat:
		print("Password is valid.")
	else:
		print("Re-enter a new password.")
    
#email validation

def check_email(userid):
   
   regex = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'
   
   if(re.fullmatch(regex, email)):
      print("Valid Email")
      
   else:
      print("Invalid Email")

#start of program

def choose():
   choise = int(input("Press 1 for Signup \nPress 2 for Signin"))
   
   if choise == 1:
      return register()
   
   elif choise == 2:
      return Signing_In()
   
   else:
      return "\nPlease re-enter your choise correctly"

#For Sign UP

def register():
   return "\nSuccessful"

#For Sign In

def Signing_In():
   return "\nWelcome Back"
   
   
print(choose())
