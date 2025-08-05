import openai

# 🔐 Replace with your own API key
openai.api_key = "YOUR_API_KEY_HERE"

def chat():
    print("🤖 ChatGPT: Hello! Ask me anything. Type 'exit' to stop.")

    conversation = []

    while True:
        user_input = input("👤 You: ")
        if user_input.lower() in ["exit", "quit", "bye"]:
            print("🤖 ChatGPT: Goodbye! 👋")
            break

        conversation.append({"role": "user", "content": user_input})

        try:
            response = openai.ChatCompletion.create(
                model="gpt-3.5-turbo",  # You can use "gpt-4" if your account has access
                messages=conversation
            )
            message = response['choices'][0]['message']['content']
            print(f"🤖 ChatGPT: {message}")

            # Add ChatGPT response to conversation
            conversation.append({"role": "assistant", "content": message})

        except Exception as e:
            pr

