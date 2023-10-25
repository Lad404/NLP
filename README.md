# NLP
 Project 1: AI Desktop Voice Assistant

 What can this A.I. assistant do for you?
 It can send emails on your behalf.
 It can play music for you.
 It can do Wikipedia searches for you.
 It is capable of opening websites like Google, Youtube, etc., in a web browser.

 Let's start building our own AI Voice Assistant.

 Start a new project and make a file called vivi.py(Choose any name as you wish!)

  # Defining Speak Function
 The first and foremost thing for an A.I. assistant is that it should be able to speak. To make our VIVI talk, we will make a function called
 speak(). This function will take audio as an argument, and then it will pronounce it.
 def speak(audio):
 pass      
#For now, we will write the conditions later.

Now, the next thing we need is audio. We must supply audio so that we can pronounce it using the speak() function we made. We are going to install a module called pyttsx3.

 What is pyttsx3?
 A python library that will help us to convert text to speech. In short, it is a  text-to-speech library.
 It works offline, and it is compatible with Python 2 as well as Python 3.
 Installation:
 pip install pyttsx3

  import pyttsx3
  engine = pyttsx3.init('sapi5')
  voices= engine.getProperty('voices') #getting details of current voice
  engine.setProperty('voice', voice[0].id)
 #What is sapi5?
 Microsoft developed speech API. Helps in synthesis and recognition of voice.
 What Is VoiceId?
 Voice id helps us to select different voices.
 voice[0].id = Male voice 
 voice[1].id = Female voice
 #Writing Our speak() Function :
 We made a function called speak() at the starting. Now, we will write our speak() function to convert our text to speech.
 def speak(audio):
 engine.say(audio) 
engine.runAndWait() #Without this command, speech will not be audible to

 # Creating Our main() function: 
We will create a main() function, and inside this main() Function, we will
 call our speak function.
 Code:
 if __name__=="__main__" :
 speak(" ")

Whatever you will write inside this speak() function will be converted into speech.

# Defining Wish me Function :
 Now, we will make a wishme() function that will make our J.A.R.V.I.S. wish or greet the user according to the time of computer or pc. To provide current
 or live time to A.I., we need to import a module called datetime. Import this module to your program by:
 import datetime
 Now, let's start defining the wishme() function:
 def wishme():
 hour = int(datetime.datetime.now().hour)
 Here, we have stored the current hour or time integer value into a variable named hour. Now, we will use this hour value inside an if-else loop. 

 # Defining Take command Function :
 The next most important thing for our A.I. assistant is that it should take command with the help of the microphone of the user's system. So, now
 we will make a takeCommand() function.  With the help of the takeCommand() function, our A.I. assistant will return a string output by taking microphone input from the user.
 Before defining the takeCommand() function, we need to install a module called speechRecognition. Install this module by
 pip install speechRecognition

 After successfully installing this module, import this module into the program by writing an import statement.
 import speechRecognition as sr

 Let's start coding the takeCommand() function :
 def takeCommand():
 #It takes microphone input from the user and returns string output
    r 
= sr.Recognizer()
 with sr.Microphone() as source:
 print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)
 We have successfully created our takeCommand() function. Now we are going to add a try and except block to our program to handle errors effectively.
 try:
 print("Recognizing...")    
        query = r.recognize_google(audio, language='en-in') #Using googl
 print(f"User said: {query}\n")  #User query will be printed.
 except Exception as e:
 # print(e)    
print("Say that again please...")   
#Say that again will be printed
 return "None" #None string will be returned
 return query

 To do Wikipedia searches, we need to install and import the Wikipedia module into our program. Type the below command to install the
 Wikipedia module :
 pip install wikipedia
 After successfully installing the Wikipedia module, import it into the
 program by writing an import statement.
 if __name__ == "__main__":
    wishMe()
 while True:
 # if 1:
        query = takeCommand().lower() #Converting user query into lower 
# Logic for executing tasks based on query
 if 'wikipedia' in query:  #if wikipedia found in the query then 
            speak('Searching Wikipedia...')
            query 
= query.replace("wikipedia", "")
            results = wikipedia.summary(query, sentences=2) 
            speak("According to Wikipedia")
 print(results)
            speak(results)
 In the above code, we have used an if statement to check whether Wikipedia is in the user's search query or not. If Wikipedia is found in the user's search query, then two sentences from the summary of the Wikipedia page will be converted to speech with the speak function's help.
 31:24 – Defining Task 2: To open YouTube site in a web-browser
 To open any website, we need to import a module called webbrowser. It is an in-built module, and we do not need to install it with a pip statement; we can directly import it into our program by writing an import statement.
 Code: 
elif 'open youtube' in query:
            webbrowser.open("youtube.com")

# Defining Task 3: To open Google site in a web-browser
 elif 'open google' in query:
            webbrowser.open("google.com")
 We are opening Google in a web-browser by applying the same logic that we used to open youtube. 

# Defining Task 4: To play music 
To play music, we need to import a module called os. Import this module
 directly with an import statement.
    elif 'play music' in query:
            music_dir = '(Your file path)'
            songs = os.listdir(music_dir)
            print(songs)    
            os.startfile(os.path.join(music_dir, songs[0])) 

# Defining Task 5: To know the current time
 elif 'the time' in query:
            strTime = datetime.datetime.now().strftime("%H:%M:%S")    
            speak(f"Sir, the time is {strTime}")

# Steps to get the code path of the application:
 Step 1: Open the file location.
 Step 2: Right-click on the application and click on properties.
 Step 3: Copy the target from the target section.
 After copying the target of the application, save the target into a variable. Here, I am saving the target into a variable called codePath, and then we
 are using the os module to open the application.

 elif 'open code' in query:
            codePath = "Your File Path"
            os.startfile(codePath)



# Defining Task 7: To send Email
 To send an email, we need to import a module called smtplib.
 What is smtplib?
 Simple Mail Transfer Protocol (SMTP) is a protocol that allows us to send emails and route emails between mail servers. An instance method called sendmail is present in the SMTP module. This instance method allows us to send an email.  It takes 3 parameters:
 The sender: Email address of the sender.
 The receiver: T Email of the receiver.
 The message: A string message which needs to be sent to one or more than one recipient.

# Defining Send email function :
 We will create a sendEmail() function, which will help us send emails to
 one or more than one recipient.
 def sendEmail(to, content):
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.ehlo()
        server.starttls()
    server.login('youremail@gmail.com', 'your-password')
    server.sendmail('youremail@gmail.com', to, content)
    server.close()
 
 # Recapitulate
 1. First of all, we have created a wishme() function that gives the greeting functionality according to our A.I system time.
 2. After wishme() function, we have created a takeCommand() function, which helps our A.I to take command from the user. This function is also
 responsible for returning the user's query in a string format.
 3. We developed the code logic for opening different websites like google, youtube, and stack overflow.
 4. Developed code logic for opening VS Code or any other application.
 5. At last, we added functionality to send emails.
 