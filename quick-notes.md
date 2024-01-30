# quick notes about forms and crud in django web framework :
here is some notes about django forms and crud operations :

## general
#### how django forms work :
when you create a class and inherit from `forms.Form`, you declare some fields. and django only builds the inputs for us and not the form tag or buttons. only inputs and labels corresponding to the fields we defined.
so in order to actually use those inputs you need to put the `{{form}}` into a html form tag.

other thing to note is that django renders forms as tables in the html by default. you can use `.as_p` to render a form as a <p> tags in html.

#### bounding forms in views :
normally in get methods we don't bound our forms. it means we don't pass any data as parameters to an instance of a form class. unless if you want to display data in a form of an editing page. in this situations you can get the instance and pass it to the `instance` parameter of a form. you can also pass the data using dictionray data type.

## fields
you can see more info about fields from here https://docs.djangoproject.com/en/5.0/ref/forms/fields/ .


## widgets
you can see more info about fields from here https://docs.djangoproject.com/en/5.0/ref/forms/widgets/


## how to add style or class to your fileds through a form class | attrs:



## how to change an error message of an input through a form class :
...
