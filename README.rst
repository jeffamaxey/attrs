.. raw:: html

   <p align="center">
      <a href="https://www.attrs.org/">
         <picture>
            <source srcset="./docs/_static/attrs_logo_white.svg" media="(prefers-color-scheme: dark)">
            <img src="./docs/_static/attrs_logo.svg" width="35%" alt="attrs" />
         </picture>
      </a>
   </p>
   <p align="center">
      <a href="https://www.attrs.org/en/stable/?badge=stable">
          <img src="https://img.shields.io/badge/Docs-Read%20The%20Docs-black" alt="Documentation" />
      </a>
      <a href="https://github.com/python-attrs/attrs/blob/main/LICENSE">
         <img src="https://img.shields.io/badge/license-MIT-C06524" alt="License: MIT" />
      </a>
      <a href="https://pypi.org/project/attrs/">
         <img src="https://img.shields.io/pypi/v/attrs" />
      </a>
      <a href="https://pepy.tech/project/attrs">
         <img src="https://static.pepy.tech/personalized-badge/attrs?period=month&units=international_system&left_color=grey&right_color=blue&left_text=Downloads%20/%20Month" alt="Downloads per month" />
      </a>
      <a href="https://zenodo.org/badge/latestdoi/29918975"><img src="https://zenodo.org/badge/29918975.svg" alt="DOI"></a>
   </p>

.. teaser-begin

``attrs`` is the Python package that will bring back the **joy** of **writing classes** by relieving you from the drudgery of implementing object protocols (aka `dunder methods <https://www.attrs.org/en/latest/glossary.html#term-dunder-methods>`_).
`Trusted by NASA <https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#list-of-qualifying-repositories-for-mars-2020-helicopter-contributor-achievement>`_ for Mars missions since 2020!

Its main goal is to help you to write **concise** and **correct** software without slowing down your code.

.. teaser-end

For that, it gives you a class decorator and a way to declaratively define the attributes on that class:

.. -code-begin-

.. code-block:: pycon

   >>> from attrs import asdict, define, make_class, Factory

   >>> @define
   ... class SomeClass:
   ...     a_number: int = 42
   ...     list_of_numbers: list[int] = Factory(list)
   ...
   ...     def hard_math(self, another_number):
   ...         return self.a_number + sum(self.list_of_numbers) * another_number


   >>> sc = SomeClass(1, [1, 2, 3])
   >>> sc
   SomeClass(a_number=1, list_of_numbers=[1, 2, 3])

   >>> sc.hard_math(3)
   19
   >>> sc == SomeClass(1, [1, 2, 3])
   True
   >>> sc != SomeClass(2, [3, 2, 1])
   True

   >>> asdict(sc)
   {'a_number': 1, 'list_of_numbers': [1, 2, 3]}

   >>> SomeClass()
   SomeClass(a_number=42, list_of_numbers=[])

   >>> C = make_class("C", ["a", "b"])
   >>> C("foo", "bar")
   C(a='foo', b='bar')


After *declaring* your attributes, ``attrs`` gives you:

- a concise and explicit overview of the class's attributes,
- a nice human-readable ``__repr__``,
- equality-checking methods,
- an initializer,
- and much more,

*without* writing dull boilerplate code again and again and *without* runtime performance penalties.

**Hate type annotations**!?
No problem!
Types are entirely **optional** with ``attrs``.
Simply assign ``attrs.field()`` to the attributes instead of annotating them with types.

----

This example uses ``attrs``'s modern APIs that have been introduced in version 20.1.0, and the ``attrs`` package import name that has been added in version 21.3.0.
The classic APIs (``@attr.s``, ``attr.ib``, plus their serious-business aliases) and the ``attr`` package import name will remain **indefinitely**.

Please check out `On The Core API Names <https://www.attrs.org/en/latest/names.html>`_ for a more in-depth explanation.


Data Classes
============

On the tin, ``attrs`` might remind you of ``dataclasses`` (and indeed, ``dataclasses`` `are a descendant <https://hynek.me/articles/import-attrs/>`_ of ``attrs``).
In practice it does a lot more and is more flexible.
For instance it allows you to define `special handling of NumPy arrays for equality checks <https://www.attrs.org/en/stable/comparison.html#customization>`_, or allows more ways to `plug into the initialization process <https://www.attrs.org/en/stable/init.html#hooking-yourself-into-initialization>`_.

For more details, please refer to our `comparison page <https://www.attrs.org/en/stable/why.html#data-classes>`_.

.. -project-information-

Project Information
===================

- **License**: `MIT <https://choosealicense.com/licenses/mit/>`_
- **PyPI**: https://pypi.org/project/attrs/
- **Source Code**: https://github.com/python-attrs/attrs
- **Documentation**: https://www.attrs.org/
- **Changelog**: https://www.attrs.org/en/stable/changelog.html
- **Get Help**: please use the ``python-attrs`` tag on `StackOverflow <https://stackoverflow.com/questions/tagged/python-attrs>`_
- **Contributing**: https://github.com/python-attrs/attrs/blob/main/.github/CONTRIBUTING.md
- **Third-party Extensions**: https://github.com/python-attrs/attrs/wiki/Extensions-to-attrs
- **Supported Python Versions**: 3.6 and later (last 2.7-compatible release is `21.4.0 <https://pypi.org/project/attrs/21.4.0/>`_)


``attrs`` for Enterprise
------------------------

Available as part of the Tidelift Subscription.

The maintainers of ``attrs`` and thousands of other packages are working with Tidelift to deliver commercial support and maintenance for the open source packages you use to build your applications.
Save time, reduce risk, and improve code health, while paying the maintainers of the exact packages you use.
`Learn more. <https://tidelift.com/subscription/pkg/pypi-attrs?utm_source=pypi-attrs&utm_medium=referral&utm_campaign=enterprise&utm_term=repo>`_
