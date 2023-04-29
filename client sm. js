<!DOCTYPE html>
<html>
<head>
	<title>Social Media Web Application</title>
	<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
	<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
</head>
<body>
	<h1>Welcome to the Social Media Web Application!</h1>

	<form id="post-form">
		<label for="post">Write a post:</label><br>
		<textarea id="post" name="post" rows="4" cols="50"></textarea><br>
		<button type="submit">Post</button>
	</form>

	<hr>

	<div id="posts">
		<!-- Posts will be dynamically added here -->
	</div>

	<script>
		// Get all existing posts on page load
		fetchPosts();

		// Helper function to fetch all existing posts
		function fetchPosts() {
			axios.get('/api/posts')
				.then(function(response) {
					displayPosts(response.data);
				})
				.catch(function(error) {
					console.log(error);
				});
		}

		// Helper function to display all posts in the DOM
		function displayPosts(posts) {
			var content = '';
			for (var i = 0; i < posts.length; i++) {
				content += '<div><p>' + posts[i].text + '</p></div>';
			}
			$('#posts').html(content);
		}

		// Add a new post when the form is submitted
		$('#post-form').submit(function(event) {
			event.preventDefault();
			var postText = $('#post').val();
			if (postText.trim()) {
				axios.post('/api/posts', { text: postText })
					.then(function(response) {
						fetchPosts();
						$('#post').val('');
					})
					.catch(function(error) {
						console.log(error);
					});
			}
		});

	</script>
</body>
</html>
