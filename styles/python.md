  * Use explicit Python error handling with try/except, and avoid catching broad exceptions like Exception unless absolutely necessary in Python code.
  * Include Python-style docstrings for all public functions and classes using triple double quotes (""") according to Python conventions.
  * Prefer Python composition over inheritance; use Python mixins or dependency injection for reusable behavior rather than subclassing.
  * Keep Python functions under 50 lines; break large Python functions into smaller, reusable helpers to maintain readability.
  * Use pytest for Python testing with assert statements and leverage Python plugins like pytest-mock or pytest-django.
  * Avoid implementing Python magic methods unless you’re using well-known Python protocols like __repr__ or __eq__.
  * Use Python type hints and tools like mypy for adding static type safety to your Python codebase.
  * Use Python data modeling tools like pydantic or dataclasses instead of deep Python class hierarchies.
  * Raise custom Python exceptions for domain-specific errors, and document these Python exceptions clearly.
  * Avoid using bare except: clauses in Python; always specify the Python exception type to be caught.