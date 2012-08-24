========
 README
========

standup is an app to log daily status updates.
It is currently in super early active development, check back later.

We developed it with the following priorities:

1. Let's the team, stake holders and everyone else see status for team
   members across projects.

2. Let's us do that asynchronously. Conference calls were getting
   difficult to schedule because of the range of timezones we're in.

3. Let's us see who's blocked on what---then scrummasters can go
   through and work to unblock people.


Hacking
=======

To setup a local dev environment for hacking::

1. Create and activate a new virtual environment.
2. Clone the repo::

    $ git clone git://github.com/rlr/standup.git
    $ cd standup

3. Install required dependencies::

    $ pip install -r requirements.txt

4. Configure::

    $ cp standup/settings.py standup/local_settings.py
    $ vim ./standup/local_settings.py

5. Enable and run migrations::

    $ ./standup/migrations.py version_control
    $ ./standup/migrations.py upgrade

6. Run the app::

    $ python standup/app.py


Oh, but wait--what can you do with it? Well, for testing purposes, you
can use the included ``scripts/standup-cmd`` which is a command-line
tool you can use to create statuses.

Example::

    $ ./scripts/standup-cmd localhost:5000 ou812 willkg sumo "hi!"

(Assumes your api_key is set to ou812.)


Migrations
==========

To run migrations use::

  $ ./standup/migrations.py upgrade


Configuration
=============

These are things you can set in ``standup/local_settings.py``:

    API_KEY
        The key used for using the API. You use this for the standup-irc
        bot as well as the standup-cli.

        Defaults to something ridiculous.

    DEBUG
        Either ``True`` or ``False``. Determines whether it prints lots of
        stuff to the console and whether errors get a debugging-friendly
        error page.

        Defaults to ``False``.

These are things you can set in the environment when you launch standup:

    DATABASE_URL
        The uri to use for the database.

        Defaults to ``sqlite:///standup_app.db``.


Testing
=======

We use nose for testing. To run the tests, do::

    $ nosetests
