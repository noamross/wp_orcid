ORCiD Plugin for Wordpress
==========================

This is the development repo for a plugin I'm developing for academics to pull
their ORCiD information into wordpress blogs.

This is my first time developing a Wordpress plugin and I have limited PHP
knowledge, so collaborators are welcome. Please fork this document, add your two
cents as issues, or just hit me at [@noamross](http://twitter.com/noamross).

Design Notes
============

Overall Motivation and Goal
---------------------------

Maintaining a public list of your publications on a website is an enormous pain
in the ass. Right now, the main services for doing this are closed systems where
the author sets us a profile page within the specialty social network (e.g.,
[academia.edu](http://www.academia.edu/), ResearchGate, Mendeley), or are manual
tools for entering metadata, sometimes through BibTeX import, onto a personal
web page.

[ORCiD](http://orcid.org/) seems like the the most likely platform that will
allow researchers to maintain a permanent record of publications that is tightly
linked with other indexing services. It's working closely with many publishers
and institutions, and has APIs that allow other services to access the data.
Ideally, it should not require authors to maintain their record at all, as new
publications will automatically be added and maintained by publishers. Hopefully
the networks above will adopt it, too.

Many academics use Wordpress to maintain their home page, which is the most
broadly adopted website/blogging platform, is open source, and is supported by
many web hosts. While other systems (e.g., [Jekyll](http://jekyllrb.com/)) are
the new hotness and are growing in popularity among tech-oriented academics,
Wordpress lets users be users and developers be developers.

The goal of this plugin is to allow authors to use ORCiD as the primary record
of works, but have control over their professional website and display them as
desired. It should also be usable other web use cases, like research group
webpages.

To the extent possible, I wish to share frameworks and tools that will allow
code sharing and migration among other platforms (e.g., Drupal, Jekyll).

Features desired (in roughly descending order of priority)
----------------------------------------------------------

-   Simple UI for most users, good options, API and documentation for geeks.
-   Include your ORCiD as part of user metadata
    -   Several plugins allow custom fields already. [Martin
        Fenner's](https://github.com/mfenner/contact-info-options) includes
        ORCiD. Make compatible or just lift the code?
        -   How about allow advanced option: If `user_meta` already includes
            ORCiD from another plugin, please specify field name.

-   Import your works from ORCiD and store in the WP database, with fields for
    each part of the metadata
    -   Give option to automatically sync with ORCiD
    -   Allow additional fields for works, e.g., links to press coverage and
        other author websites, self-hosted PDFs

-   Display ORCiD works on author/user profile page
    -   Format reference for display as desired (using [citation style
        language](http://citationstyles.org/), most likely)
        -   Allow user to select from list or otherwise select within the
            interface, rather than downloading/messing with CSL

    -   A small thing, but many people want: highlight/bold the user's name
        within the list of authors
    -   Include [COinS metadata](http://ocoins.info/)

-   Filter works. For instance, display only peer-reviewed or figshare works.
-   Integrate other services that use ORCiD. For instance, display
    Altmetric/ImpactStory info based on ORCiD.
-   Allow to easily integrate into a theme, (for instance the [Openscience
    theme](https://github.com/skasberger/openscience-wordpress-theme)), so that
    it can be used on wordpress.org, and not just self-hosted websites
-   Compatibility with complementary academic wordpress tools, such as
    [kcite](http://wordpress.org/plugins/kcite/)
-   Compatibility with overlapping wordpress tools, such as
    [teachPress](http://wordpress.org/plugins/teachpress/) and
    [BibliPlug](http://wordpress.org/plugins/enhanced-bibliplug/), or at least a
    transprent enough codebase that other plugin authors can use the code.

Other considerations
--------------------

-   [Mendeley Plugin](http://wordpress.org/plugins/mendeleyplugin/): Has a lot
    of similar functionality. Could probably use some of code base. Also
    consider how they will work together if Mendeley adopts ORCiD.
-   [BibTeX Importer](https://github.com/mfenner/bibtex-importer) has code for
    the internal docs database.
-   Here's the [specification for publication
    data](http://support.orcid.org/knowledgebase/articles/118024#orcid-activities)
    from ORCiD. Note that this doesn't contain all the citation fields, but a
    text citation. An identifier field contains the DOI.
    -   Perhaps we should just store the text citation, rather than trying to
        parse the citation information. Could still add supplemental info this
        way.

-   [citeproc.php](https://bitbucket.org/rjerome/citeproc-php) could be used to
    parse citations.
