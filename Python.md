# Python programming language

The general suggestion of writing tests applies here. Try to test all of the code that is being written and don't delay that for later (it will not get easier).

## Code style

As most of the other projects written in Python, we use [PEP 8](https://www.python.org/dev/peps/pep-0008/). Though, we ignore some of the recomendations:

* Maximum line length (79 characters). The general limit we have is somewhere around 120-130.

*Reccomended video: "[Beyond PEP 8 -- Best practices for beautiful intelligible code](https://www.youtube.com/watch?v=wf-BqAjZb8M)" by Raymond Hettinger at PyCon 2015, which talks about the famous P versus NP problem.*

The general idea is to make the code within a project consistent and easy to interpret (for humans).

### Docstrings

Unless the function is easy to understand quickly, it should have a docstring describing what it does, how it does it, what the arguments are, and what the expected output is.

Most of our Python projects use "Google-style" docstrings: https://google.github.io/styleguide/pyguide.html?showone=Comments#Comments.

### SQL

TODO: How to write and format SQL queries (with and without using SQLAlchemy).

```python
result = connection.execute(sqlalchemy.text("""
    SELECT id,
           display_name,
           email,
           created,
           musicbrainz_id,
           show_gravatar
      FROM "user"
     WHERE musicbrainz_id IN :musicbrainz_usernames
"""), {
    'musicbrainz_usernames': tuple(usernames),
})
```
