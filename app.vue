<script setup>
import { useChat } from "ai/vue";

const { messages, input, handleInputChange, handleSubmit } = useChat();
</script>

<template>
  <div class="bg-gray-800 h-screen text-white">
    <div class="flex flex-col w-full max-w-md py-24 mx-auto stretch">
      <div
        v-for="message in messages"
        :key="message.id"
        class="whitespace-pre-wrap"
      >
        <Icon
          :name="
            message.role === 'user'
              ? 'solar:user-linear'
              : 'solar:soundwave-square-line-duotone'
          "
        />
        {{ message.role === "user" ? "User: " : "AI: " }}
        {{ message.content }}
      </div>

      <form @submit="handleSubmit">
        <input
          v-model="input"
          class="fixed bottom-0 w-full max-w-md p-2 mb-8 border border-gray-300 rounded-lg shadow-xl"
          placeholder="Say something..."
          @change="handleInputChange"
        />
      </form>
    </div>
  </div>
</template>
