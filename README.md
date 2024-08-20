    except sr.UnknownValueError:
        print("Sorry, I could not understand the audio.")
    except sr.RequestError as e:
        print(f"Could not request results from Google Speech Recognition service; {e}")
    except Exception as e:
        print(f"An error occurred: {e}")
    return command
def intro():
    talk('welcome back master Aryan.. i am your virtual assistance nexa... How can i assist you?? ')
    print('welcome back master Aryan.. i am your virtual assistance nexa How can i assist you?? ')
    return

def run_nexa():
    command = take_command()
    if 'play' in command:
        song = command.replace('play', '')
        talk('playing ' + song)
        pywhatkit.playonyt(song)
    elif 'time' in command:
        time = datetime.datetime.now().strftime('%I:%M %p')
        print(time)
        talk('Current time is ' + time)
    elif 'who is' in command:
        try:
            person = command.replace('who is', '').strip()
            info = wikipedia.summary(person, sentences=1)
            print(info)
            talk(info)
        except wikipedia.exceptions.DisambiguationError as e:
            talk("There are multiple results for that name. Can you be more specific?")
            print(f"Disambiguation error: {e.options}")
        except wikipedia.exceptions.PageError:
            talk("Sorry, I couldn't find any information on that person.")
            print("Page error: No match found.")
        except Exception as e:
            talk("Something went wrong.")
            print(f"An error occurred: {e}")
    elif 'date' in command:
        talk('Sorry, I have a headache, I respect your feelings but I am sorry boss')
        print('Sorry, I have a headache, I respect your feelings but I am sorry boss')
    elif 'are you single' in command:
        talk('I am in a relationship with wifi')
        print('I am in a relationship with wifi')
    elif 'joke' in command:
        joke = pyjokes.get_joke()
        talk(joke)
        print(joke)
    elif 'stop' in command:  # This is the command that will break the loop
        talk("Okay goodbye master")
        print("Stopping the assistant.")
        return True
    else:
        talk('Please say the command again.')
intro()
while True:
    if run_nexa():
        break
        # NEXA
Home automation 
