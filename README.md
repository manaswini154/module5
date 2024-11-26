<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Restaurant</title>
  <link rel="stylesheet" href="css/styles.css">
</head>
<style>
  body {
  font-family: Arial, sans-serif;
}

#main-content {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f4f4f4;
}

#specials-tile {
  padding: 20px;
  background: #ff9800;
  color: white;
  text-align: center;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

#specials-tile a {
  color: white;
  text-decoration: none;
  font-size: 20px;
}
</style>
<script> (function (global) {
  var dc = {};
  
  // Categories placeholder
  var categories = [
    { short_name: "L", name: "Lunch" },
    { short_name: "D", name: "Dinner" },
    { short_name: "S", name: "Sushi" }
  ];

  // TODO: STEP 0
  // Function to fetch categories (can be replaced with an API call if needed)
  function getCategories() {
    return categories;
  }

  // TODO: STEP 1
  // Function to select a random category
  function getRandomCategory(categories) {
    var randomIndex = Math.floor(Math.random() * categories.length);
    return categories[randomIndex].short_name;
  }

  // TODO: STEP 2
  // Dynamically set the Specials tile behavior
  document.addEventListener("DOMContentLoaded", function () {
    var specialsTile = document.querySelector("#specials-tile a");

    if (specialsTile) {
      // Fetch categories and set a random category
      var categories = getCategories();
      var randomCategoryShortName = getRandomCategory(categories);
      specialsTile.setAttribute(
        "onclick",
        "$dc.loadMenuItems('" + randomCategoryShortName + "');"
      );
    }
  });

  // Mock loadMenuItems function for demo purposes
  dc.loadMenuItems = function (shortName) {
    alert("Loading menu items for category: " + shortName);
  };

  global.$dc = dc;
})(window);
</script>
<script type="text/javascript"></script>
<body>
  <div id="main-content">
    <div id="specials-tile">
      <a href="#" onclick="$dc.loadMenuItems('{{randomCategoryShortName}}');">Specials</a>
    </div>
  </div>
  <script src="js/script.js"></script>
</body>
</html>
