# Stress Relieving Assitant Using Python
With the help of Python & Visual Studio Code we have built an Assitant which Aids you in day-to-day online tasks making you feel relaxed and ultimately calming your neurological system (stress). This Assistant will be able to open apps, tell you meditation techniques, tell you jokes when you really need them & be able to help with breathing exercises. This Assitant will have many more features in the future and we look forward to have you using our Assitant. The source code of the assistant will be provided.

Here is the code (Note that it may not work on all laptops consider installing the modules in the code):

import pyttsx3
import subprocess
import random
import time

# Initialize the text-to-speech engine
engine = pyttsx3.init()
engine.setProperty('rate', 150)

def speak(text):
    """Use the TTS engine to speak the provided text."""
    engine.say(text)
    engine.runAndWait()

def open_app(app_name):
    """Open a specified application using macOS's 'open' command."""
    try:
        subprocess.run(["open", "-a", app_name])
        speak(f"Opening {app_name}.")
    except Exception as e:
        speak(f"Sorry, I couldn't open {app_name}. Error: {str(e)}")

def random_stress_relief():
    """Return a random stress relief technique."""
    stress_relief_techniques = [
        "Take a few deep breaths.",
        "Go for a walk outside.",
        "Listen to your favorite music.",
        "Try a short meditation session.",
        "Do some light stretching or yoga.",
        "Write down your thoughts in a journal.",
        "Spend time with a pet or loved one.",
        "Watch a funny movie or show.",
        "Make a cup of herbal tea and relax.",
        "Practice mindfulness or focus on the present moment."
    ]
    return random.choice(stress_relief_techniques)

def tell_joke():
    """Tell a random joke."""
    jokes = [
        "Why did the math book look sad? Because it had too many problems.",
        "Why don’t scientists trust atoms? Because they make up everything!",
        "What do you call fake spaghetti? An impasta!",
        "Why was the computer cold? It left its Windows open!",
        "Why did the scarecrow win an award? Because he was outstanding in his field!"
    ]
    joke = random.choice(jokes)
    speak(joke)

def deep_breathing_exercise():
    """Guide the user through a deep breathing exercise."""
    speak("Let's start a deep breathing exercise. Breathe in...")
    time.sleep(4)
    speak("Hold it...")
    time.sleep(2)
    speak("And breathe out...")
    time.sleep(4)
    speak("Repeat this a few times to feel more relaxed.")



def main():
    """Main function to run the AI assistant."""
    speak("Hello! I am your assistant. Type 'wake up' to activate me.")

    while True:
        command = input().lower()
        if command == "wake up":
            speak("I am awake! How can I help you today?")
            while True:
                command = input("Type a command (open, relieve stress, joke, breathe, or quit): ").lower()

                if command.startswith("open "):
                    app_name = command.split("open ", 1)[1].strip()
                    open_app(app_name)
                elif command == "relieve stress":
                    technique = random_stress_relief()
                    speak(technique)
                elif command == "joke":
                    tell_joke()
                elif command == "breathe":
                    deep_breathing_exercise()
                elif command == "quit":
                    speak("Goodbye! Have a great day!")
                    return
                else:
                    speak("Sorry, I didn't understand that command. Please try again.")
        else:
            speak("Please type 'wake up' to activate the assistant.")

if __name__ == "__main__":
    main()



