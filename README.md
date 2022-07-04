# Grade-Java-Programming-Assignment-using-AI-and-Python
Grade Java Programming Assignment using Python

# Install the requirements
## Using the subprocess in Python
  ##
      pip install subprocess
      pip install os
      from difflib import SequenceMatcher as sm
      
# Code to run the java program and compare between the doctor answer and student answer
##
      import subprocess
      import os
      '''
      If you want to run C Program instead of Java , you can use this code
      def excuteC():


          data, temp = os.pipe()
          os.write(temp,bytes("5 10 20 30 40 50", "utf-8"))
          os.close(temp)

          # store the return code of the c program(return 0)
          # and display the output
          #s = subprocess.run(['java', 'RandomNumInt', '--min', 1, '--max', 100]
          s = subprocess.check_output("gcc SumOfNumbers.c -o out1;./out1",stdin=data, shell = True )
          C_Output=s.decode("utf-8")
          #C_Output=s
          print(C_Output)
      '''
      '''
      If you want to run C++ Program instead of Java , you can use this code
      def executeCpp():

          # create a pipe to a child process
          data, temp = os.pipe()

          # write to STDIN as a byte object(convert string
          # to bytes with encoding utf8)
          os.write(temp, bytes("5", "utf-8"));
          os.close(temp)

          # store output of the program as a byte string in s
          s = subprocess.check_output("g++ HelloWorld.cpp -o out2;./out2", stdin = data, shell = True)

          # decode s to a normal string
          print(s.decode("utf-8"))
      '''
      def executeJavaDoctor():
         global Java_Output_doctor
         #s = subprocess.check_output("javac SumOfNumbers2.java;java SumOfNumbers2",isinstance(input,int),subprocess.errno,stdin = data, shell = True)
         s = subprocess.getoutput("javac HelloWorldDoctor.java;java HelloWorldDoctor")
         Java_Output_doctor=s
         print("Java_Output_doctor is : " + Java_Output_doctor)

      def executeJavaStudent():
         global Java_Output_student
         #s = subprocess.check_output("javac SumOfNumbers2.java;java SumOfNumbers2",isinstance(input,int),subprocess.errno,stdin = data, shell = True)
         s = subprocess.getoutput("javac HelloWorldStudent.java;java HelloWorldStudent")
         Java_Output_student=s
         print("Java_Output_student is : " + Java_Output_student)


      # Driver function
      if __name__=="__main__":
          #excuteC()    
          #executeCpp()
          executeJavaDoctor()
          executeJavaStudent()
          similarity=sm(None,Java_Output_doctor,Java_Output_student).ratio()
          SetAssignmentDegree=input("Enter the assignment grade")
          Final_degree=similarity*int(SetAssignmentDegree)
          print(Final_degree)

    
