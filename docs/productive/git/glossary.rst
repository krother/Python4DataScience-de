.. SPDX-FileCopyrightText: 2020 Veit Schiele
..
.. SPDX-License-Identifier: BSD-3-Clause

Git-Glossar
===========

.. glossary::

    Git
        Git ist eine verteilte Versionsverwaltung

    GitLab
        Web-Anwendung zur Versionsverwaltung auf Basis von :term:`git`. Später
        kamen Gitlab CI, ein System zur kontinuierlichen Integration, GitLab
        Runner, Container-Registry und vieles andere hinzu.

    ``git commit``
        ein Snapshot des gesamten Git-Repository, komprimiert in einem `SHA
        <https://de.wikipedia.org/wiki/Secure_Hash_Algorithm>`_

    ``branch``
        ein leichtgewichtiger beweglicher Zeiger auf einen Commit

    ``clone``
        lokale Version eines Repository einschließlich aller Commits und
        Branches

    ``remote``
        gemeinsames Repository, z.B. auf GitLab, zum Austausch der Änderungen
        in einem Team

    ``fork``
        Kopie eines Repository auf GitLab, die einem anderen Nutzer gehört

    Merge request
        Ort zum Vergleichen und Diskutieren der in einem Branch eingeführten
        Änderungen mit Bewertungen, Kommentaren, Tests etc.; siehe auch
        `Merge requests
        <https://docs.gitlab.com/ee/user/project/merge_requests/>`_.

    ``HEAD``
        Der ``HEAD``-Zeiger repräsentiert euer aktuelles Arbeitsverzeichnis und
        kann mit ``git switch`` in verschiedene Zweige, Tags oder Commits
        verschoben werden

    Trunk-Based Development
    TBD
        Git-Workflow mit kurzlebigen Themenzweigen, die schnell zum einem
        einzigen ``main``-Zweig zusammengeführt werden.

        .. seealso::
           * `Trunk Based Development <https://trunkbaseddevelopment.com/>`_
