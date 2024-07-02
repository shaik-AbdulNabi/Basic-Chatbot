import nltk
import numpy as np
from nltk.tokenize import word_tokenize
from nltk.stem import WordNetLemmatizer
from nltk.corpus import stopwords

nltk.download('punkt')
nltk.download('wordnet')
nltk.download('stopwords')

# Define patterns and responses
patterns = {
    'greeting': ['hi', 'hello', 'hey', 'howdy', 'greetings'],
    'goodbye': ['bye', 'farewell', 'see you', 'adios'],
    'thanks': ['thanks', 'thank you'],
    'options': ['what can you do', 'what are your abilities'],
}

responses = {
    'greeting': ['Hello!', 'Hi there!', 'Hey!', 'Greetings!'],
    'goodbye': ['Goodbye!', 'Farewell!', 'See you later!'],
    'thanks': ['You\'re welcome!', 'No problem!', 'My pleasure!'],
    'options': ['I can have conversations with you.', 'I can answer questions.', 'Ask me anything!'],
    'fallback': ['I don\'t understand.', 'Could you repeat that?', 'Not sure I understand.']
}

# Initialize lemmatizer and stopwords
lemmatizer = WordNetLemmatizer()
stop_words = set(stopwords.words('english'))

def preprocess_sentence(sentence):
    # Tokenize the sentence
    words = word_tokenize(sentence.lower())
    # Remove stop words and lemmatize the words
    words = [lemmatizer.lemmatize(word) for word in words if word not in stop_words]
    return words

def get_intent(sentence):
    for intent, patterns_list in patterns.items():
        for pattern in patterns_list:
            if pattern in sentence:
                return intent
    return 'fallback'

def get_response(intent):
    if intent in responses:
        return np.random.choice(responses[intent])
    else:
        return np.random.choice(responses['fallback'])

def chatbot():
    print("Welcome! Ask me anything or say goodbye to exit.")
    while True:
        user_input = input("You: ").strip()
        if user_input.lower() == 'bye':
            print(get_response('goodbye'))
            break
        
        intent = get_intent(user_input)
        response = get_response(intent)
        print("Bot:", response)

if __name__ == "__main__":
    chatbot()
