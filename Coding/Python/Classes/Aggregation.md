# Aggregation

- Aggregation is often described as a weak form of [[Composition|composition]]
- In composition, the objects that another object is composed of do not exist outside of their container
- Aggregation uses existing instances
	- You would use aggregation when it's more likely you would want to swap out objects

## Example
```python
# Class using aggregation
class HtmlDoc:

    def __init__(self, doc_type, head, body):
        self._doc_type = doc_type
        self._head = head
        self._body = body

    def add_head(self, name, contents):
        self._head.add_tag(name, contents)

    def add_tag(self, name, contents):
        self._body.add_tag(name, contents)

    def display(self, file=None):
        self._doc_type.display(file=file)
        print('<html>', file=file)
        self._head.display(file=file)
        self._body.display(file=file)
        print('</html>', file=file)


# Supporting classes
class Tag:

    def __init__(self, name, contents):
        self.start_tag = '<{}>'.format(name)
        self.end_tag = '</{}>'.format(name)
        self.contents = contents

    def __str__(self):
        return "{0.start_tag}{0.contents}{0.end_tag}".format(self)

    def display(self, file=None):
        print(self, file=file)


class DocType(Tag):

    def __init__(self):
        super().__init__('!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" http://www.w3.org/TR/html4/strict.dtd', '')
        self.end_tag = ''  # DOCTYPE does not have an end tag


class Head(Tag):

    def __init__(self):
        super().__init__('head', '')
        self._head_contents = []

    def add_tag(self, name, contents):
        new_tag = Tag(name, contents)
        self._head_contents.append(new_tag)

    def display(self, file=None):
        for tag in self._head_contents:
            self.contents += str(tag)

        super().display(file=file)


class Body(Tag):

    def __init__(self):
        super().__init__('body', '')  # Body contents will be built up separately
        self._body_contents = []

    def add_tag(self, name, contents):
        new_tag = Tag(name, contents)
        self._body_contents.append(new_tag)

    def display(self, file=None):
        for tag in self._body_contents:
            self.contents += str(tag)

        super().display(file=file)
```