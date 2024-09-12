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

    <label for="services">Services Requested:</label><br>
    <select id="services" name="services" multiple>
      <option value="AI-Driven Solutions">AI-Driven Solutions</option>
      <option value="Creative Consulting">Creative Consulting</option>
      <option value="Program & Project Management">Program & Project Management</option>
      <option value="Tech Education">Tech Education</option>
      <option value="Other">Other</option>
      <option value="Free 25 min Consult">Free 25 min Consult</option>
    </select><br><br>

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
      records: [
        {
          fields: {
            "fldhj8gNFN8YRyx0Q": document.getElementById('name').value,
            "fldV2KR2jsrOq28Nh": document.getElementById('pronouns').value,
            "fldAROLq9QOkiHNW5": document.getElementById('business').value,
            "fldW5Y4Y1Bfszai5z": "Todo", // Set initial status to "Todo"
            "fldpqwJZUWEA1mNKI": Array.from(document.getElementById('services').selectedOptions).map(option => option.value),
            "fldfOS6fuCWJRwMoM": document.getElementById('comments').value
          }
        }
      ]
    };

    // Send data to Airtable
    fetch('https://api.airtable.com/v0/appBpAOPam4bafkjY/tblsSpZwVX3QjTeA7', {
      method: 'POST',
      headers: {
        'Authorization': 'Bearer pataD2e03wwuceAVg', // Ensure your token is correct
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(formData)
    })
    .then(response => response.json())
    .then(data => {
      if (data.records) {
        alert('Your submission was successful!');
      } else {
        alert('There was an error with your submission.');
      }
    })
    .catch(error => console.error('Error:', error));
  });
</script>
