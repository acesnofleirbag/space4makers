# Python Migrations

Ever needed to create database migrations in Python and didn't know where to start?

### What's Migrations?

Migrations is a mode to realize a database versioning, the form how the database was implemented with your tables and
tables's configurations

Are very powerful and very used because permits that in 1 (one) or on max 2 (two) commands we have the database's
structure created, so much for testing or project's initialization in case of the first contact 

### Alembic

[Alembic](https://alembic.sqlalchemy.org/en/latest/) it's a Python module that give us the possibility to execute the
migrations in a easy way, we make this following the follows steps:

- alembic init 

Is used to init the alembic configuration file on project (run this command on project root folder)

```console
$ alembic init migrations
```

on this moment will be created a folder called `migrations` and the file `alembic.ini` on project root folder, go to the
file `alembic.ini` and pass the database connection string, e.g:

> This step can have variations following the project's configuration

```
sqlalchemy.url = sqlite:///database/storage.db
```

- Defining the migration

Here will be created a table to a user abstraction `User`, to this execute:

```console
$ alembic revision -m "create: users table"
```

now on the path `migrations/versios` we can find a file similar to this: `11f0db5a01cb_create_user_table.py`

editing the file on function `upgrade`, we have the following result:

```python
# ...

def upgrade():
    op.create_table(
        "users",
        sa.Column(
            "id",
            sa.String(length = 64),
            nullable = False,
            default = lambda: str(uuid4())
        ),
        sa.Column("name", sa.String(length = 255), nullable = True),
        sa.Column("email", sa.String(length = 255), nullable = False),
        sa.Column(
            "created_at",
            sa.TIMESTAMP(),
            nullable = False,
            default = lambda: datetime.today()
        ),
        sa.UniqueConstraint("id")
    )

# ...
```

and to reverse the `upgrade` action, we change the `downgrade` on the following form:

```python
# ...

def downgrade():
    op.drop_table("users")
# ...
```

It's ready, this is suficient, we have our table `users`. To execute the migration just execute:

```console
$ alembic upgrade head
```

to revert the action just run: 

```console
$ alembic downgrade base
```

### Seeds

Seeds are pre-defined data to insert on the created tables, we can perform the seeds creation editing the `upgrade`
function:

```python
from alembic import op, context

# ...

def upgrade():
    users = op.create_table(
        "users",
        sa.Column(
            "id",
            sa.String(length = 64),
            nullable = False,
            default = lambda: str(uuid4())
        ),
        sa.Column("name", sa.String(length = 255), nullable = True),
        sa.Column("email", sa.String(length = 255), nullable = False),
        sa.Column(
            "created_at",
            sa.TIMESTAMP(),
            nullable = False,
            default = lambda: datetime.today()
        ),
        sa.UniqueConstraint("id")
    )

    if context.get_x_argument(as_dictionary = True).get("seed"):
        op.bulk_insert(
            users,
            [
                {
                    "name": "Bart Simpsons",
                    "email": "bart@mail.com"
                }
            ]
        )

# ...
```

and when we need of the seeds' data it's just to execute:

```console
$ alembic -x seed=true upgrade head
$ alembic -x seed=true downgrade base
```

