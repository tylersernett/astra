<script lang='ts'>
  let firstName = '';
  let lastName = '';
  let email = '';
  let phone = '';
  let message = '';
  let preferredContact = '';

  function handleSubmit() {
    // Handle form submission logic here
    console.log('form submitted:',{
      firstName,
      lastName,
      email,
      phone,
      message,
      preferredContact,
    });
  }
</script>

<h1 class='h1'>Contact</h1>
<p>Request to meet with an Astra physician by sending a message below or call us at 817-897-5190 for new patient appointments and/or any questions.</p>
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
  <div>
    <label class="block mb-2" for='preferredContact'>Preferred Method of Contact</label>
    <div class="space-y-2">
      <label class="inline-flex items-center">
        <input
          type="radio"
          bind:group={preferredContact}
          value="phone"
          class="form-radio"
        />
        <span class="ml-2">Phone</span>
      </label>
      <label class="inline-flex items-center">
        <input
          type="radio"
          bind:group={preferredContact}
          value="email"
          class="form-radio"
        />
        <span class="ml-2">Email</span>
      </label>
    </div>
  </div>

  <!-- Submit Button -->
  <div>
    <input type="submit" class="w-full p-2 bg-blue-600 text-white rounded"/>

  </div>
</form>

<iframe title='Map of Astra locations' src="https://www.google.com/maps/d/embed?mid=1Vc4vdMJallukcKH66W59kbvEab4&ehbc=2E312F" width="640" height="480"></iframe>