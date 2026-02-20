# Composition

- Composition is when you define a class instance object as an instance variable of another class
	- The class is therefore composed of other classes and has no (or few) attributes of its own

```python
class Wing:

    def __init__(self, ratio):
        self.ratio = ratio

    def fly(self):
        if self.ratio > 1:
            print("I can fly")
        elif self.ratio == 1:
            print("This is hard work")
        else:
            print("I'll just walk")


class Duck:

    def __init__(self):
        # Example of composition (class instance as instance variable)
        # The class is composed of other classes and has no attributes of its own
        self._wing = Wing(1.8)

    def fly(self):
        self._wing.fly()
```

## Example
```python
# Class using composition
class HtmlDoc:

    def __init__(self):
        # Define attributes via composition
        # The HtmlDoc is composed of other classes
        self._doc_type = DocType()
        self._head = Head()
        self._body = Body()

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


if __name__ == '__main__':

    # Composition class example
    my_page = HtmlDoc()
    my_page.add_head('title', 'This is a title')
    my_page.add_tag('h1', 'Main heading')
    my_page.add_tag('h2', 'Sub-heading')
    my_page.add_tag('p', 'This is a paragraph that will appear on the page')
    with open('test.html', 'w') as test_doc:
        my_page.display(file=test_doc)
```
