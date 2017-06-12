<html>

<!-- Latest patch release (recommended for production) -->
<script src="http://cdn.auth0.com/js/lock/10.16.0/lock.min.js"></script>



// Initiating our Auth0Lock
var lock = new Auth0Lock(
  'RekYT6acTMzNHc6aFW7hrlm3krvE5XcG',
  'laytonco.auth0.com'
);

// Listening for the authenticated event
lock.on("authenticated", function(authResult) {
  // Use the token in authResult to getUserInfo() and save it to localStorage
  lock.getUserInfo(authResult.accessToken, function(error, profile) {
    if (error) {
      // Handle error
      return;
    }

    localStorage.setItem('accessToken', authResult.accessToken);
    localStorage.setItem('profile', JSON.stringify(profile));
  });
});


//showing the lock
document.getElementById('btn-login').addEventListener('click', function() {
  lock.show();
});


// Verify that there's a token in localStorage
var token = localStorage.getItem('accessToken');
if (token) {
  showLoggedIn();
}

// Display the user's profile
function showLoggedIn() {
  var profile = JSON.parse(localStorage.getItem('profile'));
  document.getElementById('nick').textContent = profile.nickname;
}


</html>
