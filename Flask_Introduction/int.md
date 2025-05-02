## HOW A FLASK PROJECT SHOULD LOOK LIKE


DR_CARPETS/
├── app/
│   ├── __init__.py
│   ├── routes.py
│   └── templates/
│       ├── base.html
│       ├── homepage.html
├── main.py

## base.html example


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}My Website{% endblock %}</title>

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

    <!-- Your own CSS -->
    <link rel="stylesheet" href="{{ url_for('static', filename='styles.css') }}">
</head>
<body>

    <!-- Navbar (optional) -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">DR Carpets</a>
      </div>
    </nav>

    <!-- Main Content -->
    <div class="container mt-4">
        {% block content %}
        {% endblock %}
    </div>

    <!-- Bootstrap JS (for carousel, dropdowns etc.) -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

</body>
</html>
