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
* 1-Add attributes to a specific field.
```python
class ProductForm(forms.ModelForm):

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
   
        self.fields['title'].widget.attrs['class'] = 'form-control'
        self.fields['title'].widget.attrs['placeholder'] = 'Write product title here'

    class Meta:
        model = Product
        fields = '__all__'
```

* 2-Add attributes to all fields using for loop.
```python
class ProductForm(forms.ModelForm):

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        for visible in self.visible_fields():
            visible.field.widget.attrs['class'] = 'form-control'
            visible.field.widget.attrs['placeholder'] = visible.field.label

    class Meta:
        model = Product
        fields = '__all__'
```

## how to change an error message of an input through a form class :
```python
my_default_errors = {
    'required': 'This field is required',
    'invalid': 'Enter a valid value'
}

class MyForm(forms.Form):
    some_field = forms.CharField(error_messages=my_default_errors)
    ....
```
