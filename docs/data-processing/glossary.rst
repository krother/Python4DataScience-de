.. SPDX-FileCopyrightText: 2021 Veit Schiele
..
.. SPDX-License-Identifier: BSD-3-Clause

Glossar
=======

.. glossary::

    ACID
        ACID ist ein Akronym für **A**\tomicity **C**\onsistency **I**\solation
        **D**\urability. Sie gelten als Voraussetzung für die Verlässlichkeit
        von Datenbanktransaktionen.

        Atomarität
            Eine Transaktion ist eine Folge von Datenbankoperationen, die
            entweder vollständig oder gar nicht ausgeführt werden.
        Konsistenz
            Transaktion, die nach Beendigung einen konsistenten Zustand
            hinterlässt. Dabei werden vor Abschluss der Transaktion die im
            Datenbankschema definierten Integritätsbedingungen überprüft.
        Isolation
            Nebenläufige Transaktionen dürfen sich nicht beeinflussen.
            Realisiert wird dies üblicherweise mit :term:`Locking`, das die
            Nebenläufigkeit einschränkt.
        Durability
            Daten müssen nach erfolgreicher Transaktion dauerhaft in der
            Datenbankgespeichert bleiben und kann z.B. durch das Schreiben
            eines Transaktionslogs sichergestellt werden.

    BASE
        BASE ist ein Akronym für **B**\asically **A**\vailable, **S**\oft State,
        **E**\ventually Consistent und als Gegenbegriff zu :term:`ACID`
        entstanden.

        Dabei wird ein sehr optimistischer Konsistenzbegriff verwendet, der ohne
        :term:`Locking` auskommt. Locks sind in mehrerlei Hinsicht
        problematisch, da Zugriffe nicht möglich sind, solange Datensätze durch
        andere Transaktionen gesperrt sind. Zudem ist die Übereinkunft zum
        Setzen eines Locks bereits sehr aufwändig.

        Konsistenz der Daten wird als ein Zustand betrachtet, der irgendwann
        erreicht werden kann. Dies ist die Idee der :term:`Eventual
        Consistency`.

        Konkurrierende Zugriffe werden bei BASE durch :term:`MVCC –
        Multiversion Concurrency Control` vermieden. Es gibt jedoch eine große
        Bandbreite von Lösungen für die verschiedenen verteilten
        Datenbanksysteme:

        * Causal Consistency

          ist der Konsistenz in :term:`ACID` vergleichbar.

        * Read Your Writes
        * Session Consistency
        * Monotonic Read Consistency
        * Monotonic Write Consistency

    CAP-Theorem
        CAP ist ein Akronym für **C**\onsistency, **A**\vailability
        (Verfügbarkeit) und **P**\artition Tolerance (Ausfalltoleranz). Die
        Erkenntnisse des CAP-Theorems spielen bei der Auswahl eines
        verteilten Datenbanksystems eine zentrale Rolle.

        Das CAP-Theorem besagt, dass in verteilen Systemen die drei
        Anforderungen Konsistenz, Verfügbarkeit und  Ausfalltoleranz nicht
        vollständig vereinbar und nur maximal zwei von dreien erreichbar sind.
        Für jede Anwendung muss daher individuell entschieden werden, ob eine
        CA-, CP-, AP-Applikation realisiert werden soll.

    Cassandra
        Cassandra ist ein :doc:`nosql/column-oriented-db`, und wurde
        ursprünglich von Facebook entwickelt um Suchen im E-Mail-Engang zu
        optimieren. Heute wird es unter dem Dach der `Apache Software Foundation
        <https://www.apache.org/>`_ weiterentwickelt.

        Das Datenmodell von Cassandra hat weder eine logische Struktur noch ein
        Schema. Für die Modellierung wird empfohlen *«First write your queries,
        then model your data»*. Meist wird dann eine *Column Family* für jede
        erwartete Anfrage erstellt. Dabei werden die Daten zwar denormalisiert,
        aber jede *Column Family* antwortet auf eine bestimmte Art von Anfragen.

        In Cassandra kann für jede Anfrage die Konsistenz angegeben werden. Das
        ermöglicht, dass spezifische Anfragen sehr konsistent sein können
        während andere die Konsistenz der Geschwindigkeit opfern. Für die
        Schreibkonsistenz gibt es z.B. die folgenden vier Ebenen:

        ANY
            gewährleistet, dass die Daten in mindestens einem Knoten gespeichert
            sind.
        ONE
            gewährleistet, dass die Daten im Commit-Log von mindestens einer
            Replica gespeichert sind.
        QUORUM
            gewährleistet, dass die Daten in einen Quorum von Replicas
            gespeichert sind.
        ALL
            gewährleistet, dass die Daten auf alle Replicas gespeichert sind.

        Cassandra stellt zwei verschiedene APIs zur Verfügung: `Thrift
        <https://thrift.apache.org/>`_ und `CQL (Cassandra Query Language)
        <https://cassandra.apache.org/doc/latest/cql/>`_.

    Column Family
        Column Families entsprechen Tabellen in relationalen Datenbanken. Sie
        gruppieren Spalten gleichen oder ähnlichen Inhalts, z.B.:

        .. code-block:: javascript

            profile = {
                cusy: {
                    name:       "Cusy GmbH",
                    email:      "info@cusy.io",
                    website:    "cusy.io"
                },
                veit: {
                    name:       "Veit Schiele",
                    email:      "veit.schiele@cusy.io",
                }
            }

    CouchDB
        CouchDB ein Akronym für **C**\luster **o**\f **u**\nreliable
        **c**\ommodity **h**\ardware **D**\ata **B**\ase. Dabei handelt es sich
        um ein :doc:`nosql/document-oriented-db`.

    Eventual Consistency
        *»Konsistenz als Zustandsübergang, der irgendwann erreicht wird.«*

        Der Begriff wurde für :term:`BASE` als Alternative zu :term:`ACID`
        entwickelt.

    Graph traversal
        Graph traversal wird meist zur Suche von Knoten verwendet. Es gibt
        verschiedene Algorithmen für solche Suchanfragen in einem Graphen, die
        sich grob einteilen lassen in

        * Breiten- und Tiefensuche (engl: breadth-first search, BFS und
          depth-first search, DFS)

          Die Breitensuche beginnt mit allen Nachbarknoten des Startknotens.
          Im nächsten Schritt werden dann die Nachbarn der Nachbarn durchsucht.
          Die Pfadlänge erhöht sich mit jeder Iteration.

          Die Tiefensuche verfolgt einen Pfad solange, bis ein Knoten ohne
          ausgehende Kanten gefunden wird. Der Pfad wird anschließend
          zurückverfolgt bis zu einem Knoten, der noch weitere ausgehende Kanten
          hat. Dort wird die Suche dann fortgesetzt.

        * Algorithmische Traversierung

          Beispiele für die algorithmische Traversierung sind

          * Hamiltonweg (Traveling Salesman)
          * Eulerweg
          * Dijkstra-Algorithmus

        * Randomisierte Traversierung

          Der Graph wird nicht nach einem bestimmten Schema durchlaufen, sondern
          der nächste Knoten wird zufällig ausgewählt. Dadurch kann vor allem bei
          großen Graphen wesentlich schneller ein Suchergebnis präsentieren, dieses
          ist jedoch nicht immer das beste.

    Graphenmodell
        Ein Graph besteht aus einer Menge an Knoten und Kanten. Graphen werden
        genutzt, um eine Vielfalt an Problemen durch Knoten, Kanten und ihren
        Beziehungen darzustellen, z.B. in Navigationssystemen, in denen die Wege
        in Form von Graphen gespeichert werden.

    Graphpartitionierung
        Mit Graphpartitionierung werden Graphen in kleinere Teilgraphen
        unterteilt. Dabei gibt es jedoch keine mathematisch exakte Methode, um
        die Anzahl der durchschnittenen Kanten zu minimieren, sondern nur ein
        paar heuristische Algorithmen, z.B. Clustering-Algorithmen, die stark
        vernetzte Teilgraphen zu abstrakten Knoten zusammenziehen.

        Von sich überlappenden Partitionierung spricht man bei Graphen, die
        nicht komplett geteilt werden können und in mehreren Teilgraphen
        existieren.

    HBase
        HBase ist ein :doc:`nosql/column-oriented-db`, welches auf verteilten
        Dateisystemen aufbaut und für real-time-Zugriffe auf großen
        Datenbeständen konzipiert ist.

    Hypertable
        Hypertable ist ein :doc:`nosql/column-oriented-db` und auf
        verteilten Dateisystemen basiert. Das Datenmodell ist das einer
        mehrdimensionalen Tabelle, die mit Schlüsseln durchsucht werden
        kann. Die erste Dimension ist der sog. *row-key*, die zweite die
        :term:`Column Family` die dritte Dimension der *Column Qualifier*
        und die vierte Dimension die Zeit.

    Konsistente Hashfunktion
        Konsistente Hashfunktionen minimieren die Anzahl der Neuzuordnungen, da
        bei einer Änderung nicht alle Schlüssel neu zugeordnet werden müssen
        sondern nur die Größe einer Hash-Tabelle geändert wird.

    Konsistenz
        Der Zustand einer Datenbank wird als konsistent bezeichnet, wenn die
        gespeicherten Daten alle Anforderungen for :term:`Semantische
        Integrität` erfüllen.

    Locking
        Als Locking bezeichnet man das Sperren von Daten für nebenläufige
        Transaktionen.

        Je nach Art des Zugriffs gibt es unterschiedliche Lock-Verfahren:

        * :term:`Optimistic concurrency`
        * :term:`Pessimistic locking`
        * :term:`Two-phase locking (2PL)`

    MapReduce
        MapReduce ist ein von Google Inc. 2004 eingeführtes Framework, das für
        die nebenläufige Berechnungen enorm großer Datenmengen auf
        Computerclustern verwendet wird. Es wurde durch die, in der funktionalen
        Programmierung häufig verwendeten Funktionen *map* und *reduce*
        inspiriert auch wenn die Semantik von diesen etwas abweicht.

    MongoDB
        MongoDB ist eine schemafrei :doc:`nosql/document-oriented-db`,
        die Dokumente im `BSON <https://bsonspec.org/>`_-Format verwaltet.

    MVCC – Multiversion Concurrency Control
        MVCC werden kontrolliert konkurrierende Zugriffe auf Datensätze (Lesen,
        Einfügen, Ändern, Löschen) durch verschiedene, unveränderliche Versionen
        dieser Datensätze. Die verschiedenen Versionen werden in eine zeitliche
        Reihenfolge gebracht, indem jede Version auf ihre Vorgängerversion
        verweist. MVCC hat sich gerade bei :doc:`nosql/index` zu einer zentralen
        Basistechnologie entwickelt, die es ermöglicht, konkurrierende Zugriffe
        auch ohne das :term:`Locking` von Datensätzen zu koordinieren.

    Optimistic Concurrency
        Optimistic Concurrency, auch Optimistisches Locking ist eine Form
        des :term:`Locking`, die davon ausgeht, dass wenige schreibende
        Zugriffe auf der Datenbank stattfinden und lesende Zugriffe keine
        Sperre auslösen. Bei Änderungen wird dann zunächst geprüft, ob der
        Zeitstempel seit dem Lesen der Daten unverändert geblieben ist.

    Paxos
        Paxos ist eine Familie von Protokollen zur Herstellung von Konsens in
        einem Netzwerk unzuverlässiger oder fehlbarer Prozessoren.

    Pessimistic Locking
        Pessimistic :term:`Locking` geht von vielen Schreibzugriffen auf die
        Datenbank aus. Daher sperren auch lesende Zugriffe die Daten werden
        erst wieder freigegeben, wenn die Änderungen gespeichert sind.

    Property-Graph-Modell (PGM)
        Knoten und Kanten bestehen aus Objekten mit darin eingebetteten
        Eigenschaften (Properties). Es wird nicht nur ein Wert (Label) in einer
        Kante bzw. einem Knoten gespeichert, sondern ein
        :term:`Schlüssel/Wert-Paar`.

    Riak
        Im Wesentlichen ist Riak ein dezentraler :term:`Schlüssel/Wert-Paar` mit
        einer flexiblen :term:`MapReduce`-Engine.

    Redis
        Redis ist ein :doc:`nosql/key-value-store`, die üblicherweise alle
        Daten im RAM speichert.

    Schlüssel/Wert-Paar
        Ein Wert ist immer einem bestimmten Schlüssel zugeordnet, der aus einer
        strukturierten oder willkürlichen Zeichenkette bestehen kann. Diese
        Schlüssel können in Namensräume und Datenbanken aufgeteilt werden. Die
        Werte können neben Strings auch Listen, Sets oder Hashes enthalten.

    Semantische Integrität
        Semantische Integrität ist immer dann gegeben, wenn die Eingaben richtig
        und in sich stimmig sind. Dann wird auch von konsistenten Daten
        gesprochen. Ist dies nicht der Fall, sind die Daten inkonsistent. In SQL
        kann die semantische Integrität mit ``TRIGGER`` und ``CONSTRAINT``
        überprüft werden.

    Two-phase locking (2PL)
        Das Zwei-Phasen-Sperrprotokoll unterscheidet zwei Phasen von
        Transaktionen:

        #. Die Wachstumsphase, in welcher Sperren nur gesetzt, aber nicht
           freigegeben werden dürfen.
        #. Die Schrumpfungsphase, in welcher Sperren nur freigegeben, aber
           nicht angefordert werden dürfen.

        Das Zwei-Phasen-Sperrprotokoll kennt dabei drei Sperrzustände:

        SLOCK, Shared Lock oder Read-Lock
            wird bei lesendem Zugriff auf Daten gesetzt
        XLOCK, Exclusive Lock oder Write-Lock
            wird bei schreibendem Zugriff auf Daten gesetzt
        UNLOCK
                hebt die Sperren SLOCK und XLOCK auf.

    Vektoruhr
        Eine Vektoruhr ist eine Softwarekomponente zum Zuweisen von eindeutigen
        Zeitstempeln an Nachrichten. Sie erlaubt, den Ereignissen in verteilten
        Systemen aufgrund eines Zeitstempels eine Kausalordnung zuzuweisen und
        insbesondere die Nebenläufigkeit von Ereignissen zu ermitteln.

    XPATH
        XPATH verarbeitet die Baumstruktur eines XML-Dokuments und erzeugt dabei
        Ausschnitte aus XML-Dokumenten. Um als Ergebnis vollständige
        XML-Dokumente zu erhalten, müssen diese z.B. mit :term:`XQuery` oder
        :term:`XSLT` erstellt werden. XPATH ist keine vollständige
        Abfragesprache, da sie auf Selektionen und Extraktionen beschränkt
        ist.

        XPATH ist ein Bestandteil von :term:`XQuery` seit Version 1.1 und ab
        Version 2.0 wird XPATH durch :term:`XQuery` erweitert.

    XQuery
        XQuery steht für *XML Query Language* und ist hauptsächlich eine
        funktionale Sprache, bei der während einer Abfrage auch verschachtelte
        Ausdrücke ausgewertet werden können.

    XSLT
        XSLT ist ein Akronym für **E**\xtensible **S**\tylesheet **L**\anguage
        **T**\ransformation. Mit ihr lassen sich XML-Dokumente transformieren.
