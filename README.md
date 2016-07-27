# autolink_py

The Repo extracts url/email substring from given string and converts it into
links(or any customized format).Currenty, we apply HTML and MARKDOWN replacement
type, and also apply easy way to customize the replacement.

## Installation

Installation using pip:

```
pip install autolink_py
```

##Usage

- replace URL with html format

```python
from autolink_py.core import AutoLinker

text = 'This website is google.com'

al = AutoLinker()
new_text = al.linkify(text, replaced_type='HTML')

# new_text -> 'This website is <a href="http://google.com">google.com</a>'

```

- replace URL with markdown format

```python
from autolink_py.core import AutoLinker

text = 'This website is google.com'

al = AutoLinker()
new_text = al.linkify(text, replaced_type='MARKDOWN')

# new_text -> 'This website is [google.com](http://google.com)'

```

- replace URL with customized format

```python

# example: 'google.com' -> '<google.com><http://google.com>'

from autolink_py.core import AutoLinker

class NewAutoLinker(AutoLinker):

    def replace_url(self, text, url):

        '''
        implement replace_url to customize the format you need.

        Params:
            text: url text that shown originally
            url: newly generated link including complete protocal based on text.
        '''

        return u'<{0}><{1}>'.format(text, url)

text = 'The website is google.com'

nal = NewAutoLinker()
new_text = nal.linkify(text)

# new_text -> 'The website is <google.com><http://google.com>'

```

Credits
-------

The core algorithm is referred by the open source Repo: [autolink](https://github.com/Suor/autolink)

