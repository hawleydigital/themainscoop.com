<!-- Please remove this file from your project -->
<template>
  <div class="relative flex items-top justify-center min-h-screen bg-white sm:items-center sm:pt-0">
    <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
      <h2 class="inline text-3xl font-bold tracking-tight text-gray-900 sm:block sm:text-4xl sm:tracking-tight">Something cool is coming to town.</h2>
      <p class="inline text-3xl font-bold tracking-tight text-sky-400 sm:block sm:text-4xl sm:tracking-tight">Sign up to get the scoop.</p>
      <form class="mt-8 sm:flex" id="newsletter" name="newsletter" data-netlify="true" method="POST">
        <label for="email-address" class="sr-only">Email address</label>
        <input id="email-address" name="email" type="email" autocomplete="email" required class="w-full px-5 py-3 placeholder-gray-500 focus:ring-sky-500 focus:border-sky-500 sm:max-w-xs border-gray-300 rounded-md" placeholder="Enter your email">
        <div class="mt-3 rounded-md shadow sm:mt-0 sm:ml-3 sm:flex-shrink-0">
          <button type="submit" class="w-full flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-white bg-sky-400 hover:bg-sky-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-sky-500">Give Me The Scoop</button>
        </div>
      </form>
      <!-- This example requires Tailwind CSS v2.0+ -->
      <div id="notification" class="hidden rounded-md bg-green-50 p-4 mt-12">
        <div class="flex">
          <div class="flex-shrink-0">
            <!-- Heroicon name: solid/check-circle -->
            <svg class="h-5 w-5 text-green-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
              <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
            </svg>
          </div>
          <div class="ml-3">
            <p class="text-sm font-medium text-green-800">You're on the list :)</p>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'MainScoopLandingPage',
  mounted() {
    document
      .querySelector("form")
      .addEventListener("submit", handleSubmit);

    const handleSubmit = (e) => {
      e.preventDefault();
      let myForm = document.getElementById("newsletter");
      let formData = new FormData(myForm);
      let notification = document.getElementById("notification");
      fetch("/", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
        body: new URLSearchParams(formData).toString(),
      })
        .then(() =>
          notification.classList.remove("hidden")
        )
        .catch((error) => alert(error));
    };
  }
}

</script>

