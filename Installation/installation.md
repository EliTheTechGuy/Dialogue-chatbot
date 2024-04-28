## Installation Setup

For your initial set-up you need to first 

1. Create a Dialogue flow account: First, you need to create a Dialogflow agent that will handle the conversations. This involves defining intents, entities, and dialogues that your chatbot should understand and respond to.
2. Set Up a WhatsApp Business Account with Twilio: You'll need a WhatsApp Business API account. This is different from the regular WhatsApp account or WhatsApp Business App. The WhatsApp Business API allows medium and large businesses to communicate with their customers at scale
- Create a Twilio Account: If you haven't already, sign up for an account at Twilio's website.
- Set Up WhatsApp Sandbox: Twilio provides a WhatsApp sandbox environment which allows you to test your WhatsApp integration without needing a full WhatsApp Business API account. Follow the instructions in your Twilio Console to activate and set up the sandbox. You'll need to join the sandbox by sending a code to a number provided by Twilio from your WhatsApp account.
- Get API Keys: In your Twilio console, find your Account SID and Auth Token under the ‘Project Info’ section. You will need these for authenticating API requests.
3. Integrate Dialogflow with Twilio
- In Dialogflow, go to the "Fulfillment" section.
- Enable Webhook and set the URL to your webhook handling service. This service will handle requests from Dialogflow and send them to Twilio. If you don't have a webhook handler set up, you'll need to create one. This can be a simple server that receives HTTP requests from Dialogflow and forwards them to Twilio.
- Deploy a server that can handle HTTP POST requests. This server will listen for requests from Dialogflow and call the Twilio API to send messages back to WhatsApp. You can use cloud functions (like Google Cloud Functions, AWS Lambda) or any server with a public IP.
- The server should extract the session ID (phone number) and message from Dialogflow’s request, and use Twilio’s API to send the message to the user on WhatsApp.
- In the Twilio Console, find your WhatsApp sender (the phone number you set up for WhatsApp).
- Set the webhook URL for incoming messages to point to your Dialogflow agent. This is usually the Dialogflow API that triggers intent detection.
- Configure the outbound messages (from your webhook service) to use Twilio’s ‘Messages’ API to send responses back to the user’s WhatsApp number.
