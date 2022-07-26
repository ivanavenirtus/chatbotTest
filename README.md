<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# chatbotTest

Final project for the Building AI course

## Summary

i decided to add some code to an old project i did of a chatbot for my final project in which im thinking to improve as i get more used to the python enviroment, with all that said i hope you like my project and give me some feedback on what can be done better.


## Background

Which problems does your idea solve? How common or frequent is this problem? What is your personal motivation? Why is this topic important or interesting?

This is how you make a list, if you need one:
* theres not always someone to answer or give you feedback
* im not always aware of my customers pm
* our time zones may not be the same 


## How is it used?

Describe the process of using the solution. In what kind situations is the solution needed (environment, time, etc.)? Who are the users, what kinds of needs should be taken into account? it will be added to a website were i will no longer have to worry about responding to potential clients when im not available, the code will not only make it easier but will help me keep track of names and numbers(future code)


This is how you create code examples:
```
import re
import random

def get_response(user_input):
    split_message = re.split(r'\s|[,:;.?!-_]\s*', user_input.lower())
    response = check_all_messages(split_message)
    return response

def message_probability(user_message, recognized_words, single_response=False, required_word=[]):
    message_certainty = 0
    has_required_words = True

    for word in user_message:
        if word in recognized_words:
            message_certainty +=1

    percentage = float(message_certainty) / float (len(recognized_words))

    for word in required_word:
        if word not in user_message:
            has_required_words = False
            break
    if has_required_words or single_response:
        return int(percentage * 100)
    else:
        return 0

def check_all_messages(message):
        highest_prob = {}

        def response(bot_response, list_of_words, single_response = False, required_words = []):
            nonlocal highest_prob
            highest_prob[bot_response] = message_probability(message, list_of_words, single_response, required_words)

        response('Hola', ['hola', 'klk', 'saludos', 'buenas'], single_response = True)
        response('Estoy bien y tu?', ['como', 'estas', 'va', 'vas', 'sientes'], required_words=['como'])
        response('Estamos ubicados en la vesana 102', ['ubicados', 'direccion', 'donde', 'ubicacion'], single_response=True)
        response('Siempre a la orden', ['gracias', 'te lo agradezco', 'thanks'], single_response=True)

        best_match = max(highest_prob, key=highest_prob.get)
        #print(highest_prob)

        return unknown() if highest_prob[best_match] < 1 else best_match

def unknown():
    response = ['puedes decirlo de nuevo?', 'no estoy seguro de lo quieres', 'búscalo en google a ver que tal'][random.randrange(3)]
    return response

while True:
    print("Bot: " + get_response(input('You: ')))
```


## Data sources and AI methods
Where does your data come from? Do you collect it yourself or do you use data collected by someone else?
the data is collected by the code itself with the user being the input 


## Challenges

What does your project _not_ solve? Which limitations and ethical considerations should be taken into account when deploying a solution like this?
there are lots of limitations within my code as for exaple having just a set of answers, etc. and not being able to evolve within the input feeded, the code also needs to not try to imitate human behaviour.

## What next?

How could your project grow and become something even more? What kind of skills, what kind of assistance would you  need to move on? 
adding neural networking as well as some other techniques seen during the course, like the sigmoid method, etc.


## Acknowledgments

* list here the sources of inspiration 
* do not use code, images, data etc. from others without permission
* when you have permission to use other people's materials, always mention the original creator and the open source / Creative Commons licence they've used
* etc



