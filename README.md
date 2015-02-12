### About

A simple wrapper around the orcid.org API. Enhanced clone of this rep - https://github.com/scholrly/orcid-python.

### Example


Here's a quick snippet to get info on `John Wilbanks`_. ::

    >>> import orcid
    >>> #retrieve john's profile from his ORCID
    >>> john = orcid.get('0000-0002-4510-0385')
    >>> print john.family_name
    wilbanks

What if you'd like to see an author's works or areas of interest? ::

    >>> print john.keywords
    []
    >>> print john.publications
    []

Hm, let's try another author. ::

    >>> alfonso = orcid.get('0000-0001-8855-5569')
    >>> print alfonso.keywords
    [u'computer science', u' bioinformatics', u' computational biology']
    >>> print alfonso.publications[0]
    <Publication "A note about norbert wiener and his contribution to harmonic analysis and tauberian theorems">


Maybe you'd like to read about Mr. Wiener's contributions? ::

    >>> print alfonso.publications[0].url
    http://www.scopus.com/inward/record.url?eid=2-s2.0-67650513866&partnerID=MN8TOARS

### Searching


If you'd rather search for authors, try ORCID's search functionality ::

    >>> #do a simple author search for john
    >>> authors = orcid.search('john wilbanks')
    >>> print next(authors).family_name
    wilbanks

You can also accomplish more complex queries using `Q` objects and fields ::

    >>> from orcid import Q
    >>> authors = orcid.search(Q('given-name','john') & Q('family-name', 'wilbanks'))
    >>> print next(authors).family_name
    wilbanks

Enjoy!

### Credits

Cloned from the repository https://github.com/scholrly/orcid-python lead by [Matt Luongo](https://github.com/mhluongo) from [Scholrly](https://github.com/scholrly/)
