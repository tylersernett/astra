<script lang="ts">
  let firstName = "";
  let lastName = "";
  let email = "";
  let phone = "";
  let message = "";
  let preferredContact = "";

  function handleSubmit() {
    // Handle form submission logic here
    console.log("form submitted:", {
      firstName,
      lastName,
      email,
      phone,
      message,
      preferredContact,
    });
  }
</script>

<h1 class="h1 text-center">Contact</h1>

<div class="flex flex-col md:flex-row md:space-x-8">
  <div id="form holder" class="pb-8 card shadow-md md:card-hover p-8">
    <h2 class="h3 font-bold text-center">Message Us</h2>
    <p class="py-4 text-center">
      To schedule an appointment with an Astra physician or to ask any questions, please send us a message below or call us at <a href="tel:817-897-5190">817-897-5190</a>.
    </p>
    <form on:submit|preventDefault={handleSubmit} class="space-y-4">
      <!-- First Name and Last Name Row (2 columns on medium+ screens) -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div>
          <label for="firstName" class="block mb-1">First Name</label>
          <input
            id="firstName"
            type="text"
            bind:value={firstName}
            required
            class="w-full p-2 border border-gray-300 rounded"
          />
        </div>
        <div>
          <label for="lastName" class="block mb-1">Last Name</label>
          <input
            id="lastName"
            type="text"
            bind:value={lastName}
            required
            class="w-full p-2 border border-gray-300 rounded"
          />
        </div>
      </div>

      <!-- Email Address -->
      <div>
        <label for="email" class="block mb-1">Email Address</label>
        <input
          id="email"
          type="email"
          bind:value={email}
          required
          class="w-full p-2 border border-gray-300 rounded"
        />
      </div>

      <!-- Phone Number -->
      <div>
        <label for="phone" class="block mb-1">Phone Number</label>
        <input
          id="phone"
          type="tel"
          bind:value={phone}
          required
          class="w-full p-2 border border-gray-300 rounded"
        />
      </div>

      <!-- Message -->
      <div>
        <label for="message" class="block mb-1">Message</label>
        <textarea
          id="message"
          bind:value={message}
          required
          class="w-full p-2 border border-gray-300 rounded"
          rows="4"
        ></textarea>
      </div>

      <!-- Preferred Method of Contact (Radio Buttons) -->
      <div class="flex items-center space-x-4">
        <label for="preferredContact" class="mb-0"
          >Preferred Contact Method:</label
        >
        <div class="flex space-x-4">
          <label class="inline-flex items-center">
            <input
              type="radio"
              bind:group={preferredContact}
              value="phone"
              class="form-radio"
              required
            />
            <span class="ml-2">Phone</span>
          </label>
          <label class="inline-flex items-center">
            <input
              type="radio"
              bind:group={preferredContact}
              value="email"
              class="form-radio"
              required
            />
            <span class="ml-2">Email</span>
          </label>
        </div>
      </div>

      <!-- Submit Button -->
      <div>
        <button
          type="submit"
          class="w-full p-2 btn variant-filled bg-primary-800"
        >
          Submit
        </button>
      </div>
    </form>
  </div>

  <!-- TEXT INFO -->
  <div id="text holder" class="basis-full md:basis-1/3 space-y-4">
    <div class="pt-4"><hr /></div>
    <p class="font-bold h5">Two Locations:</p>
    <div class="space-y-2">
      <p>
        <span class="font-bold">Downtown </span><br /><a
          href="https://maps.app.goo.gl/3d7W2bJQqDQMCPjE6"
          class="anchor">209 St Louis Ave, Suite 100, Fort Worth, TX 76104</a
        >
      </p>
      <p>
        <span class="font-bold">Southwest FW </span><br /><a
          href="https://maps.app.goo.gl/z3kf9HN5ssMfgt7b9"
          class="anchor">7148 Trail Lake Dr, Ft. Worth, TX 76123</a
        >
      </p>
    </div>
    <p class="font-bold h5 pt-8 md:pt-16">Network Representative:</p>
    <div class="space-y-2">
      <p>Kevin Deosarran</p>
      <p>
        New Patient Scheduling Number: <br />
        <a href="tel:817-897-5190" class="anchor">817-897-5190</a>
      </p>
    </div>
  </div>
</div>

<!-- MAP -->
<div class="mx-auto w-4/5 pb-8">
  <iframe
    title="Map of Astra locations"
    src="https://www.google.com/maps/d/embed?mid=1Vc4vdMJallukcKH66W59kbvEab4&ehbc=2E312F"
    class="w-full"
    height="480"
  ></iframe>
</div>
