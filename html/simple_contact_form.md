```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width">
	</head>
			<form action="mailto:example@example.com" method="get" enctype="text/plain">
				<label for="fname" dir="rtl">Name</label>
				<input type="text" class="fname" name="name" required></input><br>

				<label for="email" dir="rtl">Email:</label>
				<input type="email" class="email" name="email" dir="ltr" required></input><br>

				<label for="phone" dir="rtl">Telephone:</label>
				<input type="tel" class="phone" name="phone" dir="ltr" required></input><br>

				<input type="submit" class="submit" value="Send"></input>
			</form>

		</div>
	</body>
	<script src="behavior.js"></script>
</html>
```
