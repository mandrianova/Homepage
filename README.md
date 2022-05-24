# Project 0 - My homepages

Web Programming with Python and JavaScript.
In that project I introduced some information about myself for other students and colleagues.

[About the project on YouTube](https://www.youtube.com/watch?v=8IpPsb8APwU)

## Structure of the project

- The directory 'css' contents css-files from Bootsrap and styles.sass + styles.css with my personal styles for pages.
- The directory 'js' contents js-files from Bootstrap and Jquery for based functions of bootstrap.
- The directory 'img' contents all images for pages.
- The directory 'templates' contents html-templates.

## Pages

The project contents 4 pages: the main, portfolio, contacts and hobby. All of them were built using Bootstap and some custom styles.

- Home and contacts are made using columns.
- A hobby is a list.
- Portfolio is a table.

## Custom styles
- @media. I used only for printing, because for mobile I used Bootstrap.css.
- I added variables for font-family and margin-x for comfortable changing in one place for all elements.
- I added the inheritance for table, but it wasn't necessary, I think. But if I want to change the table it will be convenient and easy.
- I added special id for the name on the main page because it is not a typical headline and I removed margin-top for it in styles.

## Special hack

I created HTML pages in the previous course and it was routine and boring. And now I decided to use Jinja2 for it. These pages were created with help auto-generation. I added for it base.html and navbar.html for the general structure and the nav. Also, I used the loop for the table content.

Add my script here:

```python
from jinja2 import Environment, PackageLoader, select_autoescape


projects = [
    [2019, 'Notamedia', "Head Of Deparment", "The key department of the agency"],
    [2018, 'Notamedia', 'Project manager', "Services for the newsroom staff of the government portal"],
    [2017, 'Notamedia', 'Project manager', 'Search for the government portal'],
    [2016, 'OneAgile', 'Product Manager', "Communication Platform, Feedback system"],
    [2014, 'OneAgile', 'Product Manager', "Platform for promo-sites"],
    [2015, 'OneAgile', 'Product Manager', "Platform for promo-sites"],
    [2013, 'Smart-media', 'Head Of Department', "Formed and developed a department for the development of sites and promotional materials"],
    [2012, 'Smart-media', 'Project Manager', 'Ecommerce, Promotion sites and materials, sites for business']
]


env = Environment(
    loader=PackageLoader('project0', 'templates'),
    autoescape=select_autoescape(['html', 'xml'])
)

template_index = env.get_template("index.html")
template_contacts = env.get_template("contacts.html")
template_portfolio = env.get_template("portfolio.html")
template_hobby = env.get_template("hobby.html")


with open("../project0/templates/index.html", 'w') as index:
    index.write(template_index.render())

with open("../project0/templates/contacts.html", 'w') as contacts:
    contacts.write(template_contacts.render())

with open("../project0/templates/portfolio.html", 'w') as portfolio:
    portfolio.write(template_portfolio.render(projects=projects))

with open("../project0/templates/hobby.html", 'w') as hobby:
    hobby.write(template_hobby.render())
```
