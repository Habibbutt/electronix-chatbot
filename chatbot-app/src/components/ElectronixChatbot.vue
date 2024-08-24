<template>
  <div class="flex flex-col items-center justify-center min-h-screen bg-gray-100 p-4">
    <div class="w-full max-w-md p-4 bg-white rounded-lg shadow-md">
      <div class="flex items-center justify-between border-b pb-2 mb-4">
        <h2 class="text-xl font-semibold">Electronix Chatbot</h2>
      </div>
      <div class="chat-messages h-64 overflow-y-scroll p-2 bg-gray-50 rounded-md">
        <div class="message my-2" v-for="message in messages" :key="message.id">
          <div :class="['p-2 rounded-lg', message.isUser ? 'bg-blue-500 text-white ml-auto' : 'bg-gray-200']">
            {{ message.text }}
          </div>
        </div>
      </div>
      <div class="mt-4 flex">
        <input
          v-model="userInput"
          type="text"
          placeholder="Type your message..."
          class="flex-1 p-2 border rounded-l-md focus:outline-none"
        />
        <button
          @click="sendMessage"
          class="p-2 bg-blue-500 text-white rounded-r-md hover:bg-blue-600"
        >
          Send
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ElectronixChatbot',
  data() {
    return {
      userInput: '',
      messages: [
        { id: 1, text: 'Hello! How can I assist you today?', isUser: false },
      ],
    };
  },
  methods: {
    sendMessage() {
      if (this.userInput.trim() !== '') {
        this.messages.push({ id: this.messages.length + 1, text: this.userInput, isUser: true });
        this.userInput = '';
        // Simulate a bot response
        setTimeout(() => {
          this.messages.push({ id: this.messages.length + 1, text: 'I am here to help!', isUser: false });
        }, 1000);
      }
    },
  },
};
</script>

<style scoped>
/* Additional styles if needed */
</style>
