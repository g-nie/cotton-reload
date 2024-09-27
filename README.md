
Minimal Django project to demonstrate an issue when using [django-cotton](https://github.com/wrabit/django-cotton)
with [django-browser-reload](https://github.com/adamchainz/django-browser-reload/).

### Run

(Assuming [uv](https://github.com/astral-sh/uv) is installed)

`uv sync`

Then:

`uv run python manage.py runserver`

### Findings

I kept appending characters to the `home.html` template and waited for the refresh to
execute after every new character (`home.html` is the cotton component).

It took it 39 characters (and 39 refreshes) for the page load to need 100ms, and it kept getting worse (as monitored by the debug toolbar).
The initial page load took ~3ms on my machine.
