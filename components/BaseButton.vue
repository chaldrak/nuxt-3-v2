<template>
  <button
    type="button"
    class="whitespace-nowrap group"
    :class="buttonStyle"
  >
    <div
      class="background"
      :class="backgroundStyle"
    />
    <component
      :is="type"
      :href="href"
      :to="to"
      class="relative inline-block w-full px-2 py-2 lg:px-5 content"
      :class="contentStyle"
      :target="target"
    >
      <slot />
    </component>
  </button>
</template>

<script>
export default {
    props: {
        href: {
            type: String,
            default: ""
        },
        variant: {
            type: String,
            default: ""
        },
        underline: {
            type: Boolean,
            default: false
        },
        to: {
            type: String,
            default: ""
        },
        customBg: {
            type: String,
            default: ""
        },
        target: {
            type: String,
            default: ""
        }
    },
    computed: {
        type () {
            if (this.to) {
                return "NuxtLink";
            }
            if (this.href) {
                return "a";
            }
            return "span";
        },
        buttonStyle () {
            return this.variant ? this.variant : "default";
        },
        backgroundStyle () {
            return this.customBg ? this.customBg : this.underline ? "border-b" : "";
        },
        contentStyle () {
            return "";
        }

    }
};
</script>
<style scoped>
  /* Base */
  button {
    @apply relative inline-block;
    @apply shadow-none;
    @apply transition-shadow;
    @apply outline-none;
  }

  button .background {
    @apply absolute top-0 left-0 w-full h-full;
    @apply rounded;
    @apply transition-all duration-75 ease-out;
  }

  button:hover .background {
    @apply shadow-md;
  }

  button:disabled .background {
  }

  button:disabled {
    @apply cursor-default;
  }

  /* Default */
  .default .background {
    @apply bg-purple-500;
    @apply border-2 border-purple-500;
  }
  .default .content {
    @apply text-purple-50 font-medium;
  }
  .default:hover .background {
    @apply bg-purple-500 border-purple-300;
  }
  .default:hover .content {
    @apply text-white;
  }
  .default:disabled .background {
    @apply bg-gray-600;
  }

  /* Menu */
  .menu .content {
    @apply text-gray-300;
  }
  .menu .background {
    @apply rounded-none border-gray-500;
  }
  .menu:hover .background {
    @apply bg-gray-700 rounded;
  }
  .menu:hover .content {
    @apply text-white;
  }

  /* Text */
  .text .content {
    @apply text-purple-400 font-medium px-2;
  }
  .text .background {
    @apply border-2 border-transparent;
  }
  .text:hover .content {
    @apply text-purple-400;
  }
  .text:hover .background {
    @apply border border-purple-400;
  }

  /* Outline */
  .outline .content {
    @apply text-purple-100 font-medium;
  }
  .outline .background {
    @apply border-2 border-purple-500;
  }
  .outline:hover .content {
    @apply text-white;
  }
  .outline:hover .background {
    @apply border-purple-300;
  }
</style>
