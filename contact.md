---
title: Contact
layout: contact
description: Contact Us
permalink: /contact/
---

<form id="contact-form">
  <div>
    <label for="name">Name:</label><br>
    <input type="text" id="name" name="name" required><br><br>

    <label for="business">Business:</label><br>
    <input type="text" id="business" name="business"><br><br>

    <label for="pronouns">Preferred Pronouns:</label><br>
    <input type="text" id="pronouns" name="pronouns"><br><br>

    <label for="services">Services Interested In:</label><br>
    <select id="services" name="services">
      <option value="Creative Consulting">Creative Consulting</option>
      <option value="Program & Project Management">Program & Project Management</option>
      <option value="AI-Driven Solutions">AI-Driven Solutions</option>
      <option value="Tech Education">Tech Education</option>
      <option value="Other">Other</option>
      <option value="Free 25 min Consult">Free 25 min Consult</option>
    </select><br><br>

    <!-- Add Comments Field -->
    <label for="comments">Comments:</label><br>
    <textarea id="comments" name="comments" rows="4" cols="50"></textarea><br><br>

    <button type="submit" style="background-color: #E52F27; color: #ffffff; padding: 10px 20px; border: none; border-radius: 5px;">Contact</button>
  </div>
</form>

<script>
  document.getElementById('contact-form').addEventListener('submit', function (e) {
    e.preventDefault(); // Prevent the form from submitting normally

    // Gather form data
    const formData = {
      name: document.getElementById('name').value,
      business: document.getElementById('business').value,
      pronouns: document.getElementById('pronouns').value,
      services: document.getElementById('services').value,
      comments: document.getElementById('comments').value
    };

    // Send data to Google Sheets
    fetch('YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL', {
      method: 'POST',
      body: JSON.stringify(formData),
      headers: {
        'Content-Type': 'application/json'
      }
    })
    .then(response => response.json())
    .then(data => {
      if (data.result === 'success') {
        alert('Your submission was successful!');
      } else {
        alert('There was an error with your submission.');
      }
    })
    .catch(error => console.error('Error:', error));
  });
</script>
