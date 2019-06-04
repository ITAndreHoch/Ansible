# Jinja2

Jinja2 is templating langugage for Python (library for python)

It's an engine of templates which can contain variables
Variables is included in tex using {{ zmienna }}

**Ex:1**

```
name: Test Jinja2 Templating
  hosts: localhost
  vars:
    first_name: james
    last_name: bond
  tasks:
  - debug:
      msg: 'The name is {{ last_name }}! {{  first_name }} {{ last_name }}! '
 ```    
    
    
 Output: The name is bond! james bond!
 
 **Ex:2**
 
 ```
  name: Test Jinja2 Templating
  hosts: localhost
  vars:
    array_of_numbers:
      - 12
      - 34
      - 06
      - 34
  tasks:
  - debug:
      msg: 'Lowest = {{ array_of_numbers | min }}'
 ```
 
 Output=6
 
 # Filters:
 
 **TEXT**
 The name is {{ my_name }} => The name is Bond
 
 **Upper , lower **
 The name is {{ my_name|upper  }} => The name is BOND
 
 **Replace**
 The name is {{ my_name | replace ("Bond", "Bourne") }} => The name is Bourne
 
 
 **LIST & SET**
 **min, max**
  {{ 1,2,3,4 | min }} .  => 1
 **unique**
 {{ 1,2,3,2,3 | unique }} .  => 1
 
 **random**
 
 {{ 100|random }} .   +> random number
 
 
 
 
 **Others:**
 
 none (Test).- The none test is used to check if a variable is none, if a variable is None this tests return true.

length or count.- The length filter is used to obtain the length of a value. For example, if a variable contains latte the filter statement {{variable|length}} outputs 5. For a list variable that contains ['a','e','i'] the filter statement {{variable|length}} outputs 3.

equalto (Test).- The equalto test checks if an object has the same value as another object. For example {% if coffee.price is equalto 1.99 %} coffee prices equals 1.99 {% endif %}. This works just like the ==, but is more helpful when used with other filters such as selectattr (e.g. {{ users|selectattr("email", "equalto", "webmaster@coffeehouse.com") }}, gets users with email webmaster@coffeehouse.com).

string (Test).- The string test checks if a variable is a string (e.g. {% if variable is string %}Yes, the variable is a string!{% endif %}).

number (Test).- The number test returns true if a variable is a number.

iterable (Test).- The iterable test checks if it's possible to iterate over an object.

sequence (Test).- The sequence test checks if the object is a sequence (e.g. a generator).

mapping (Test).- The mapping test checks if the object is a mapping (e.g. a dictionary).

callable (Test).- The callable test verifies if an object is callable. In Python a function, classes and object instances with a __call__ method are callables.

sameas (Test).- The sameas test verifies if an object points to the same memory address than another object.

Strings and lists
reverse.- The reverse filter is used to get inverse representation of a value. For example, if a variable contains latte the filter statement {{variable|reverse}} generates ettal.

first.- The first filter returns the first item in a list or string. For example, for a list variable that contains ['a','e','i','o','u'] the filter statement {{variable|first}} outputs a.

join.- The join filter joins a list with a string. The join filter works just like Python's str.join(list). For example, for a list variable that contains ['a','e','i','o','u'] the filter statement {{variable|join("--)}} outputs a--e--i--o--u. The join filter also supports joining certain attributes of an object (e.g.{{ users|join(', ', attribute='username') }})

last.- The last filter returns the last item in a list or string. For example, for a list variable that contains ['a','e','i','o','u'] the filter statement {{variable|last}} outputs u.

map.- The map filter allows you to apply a filter or look up attributes, just like the standard Python map method. For example, if you have list of users but are only interested in outputting a list of usernames a map is helpful (e.g. {{ users|map(attribute='username')|join(', ') }}). In addition, it's also possible to invoke a filter by passing the name of the filter and the arguments afterwards (e.g. {{ titles|map('lower')|join(', ') }} applies the lower filter to all the elements in titles and then joins the items separated by a comma).

random.- The random filter returns a random item in a list. For example, for a list variable that contains ['a','e','i','o','u'] the filter statement {{variable|random}} could output a, e, i, o or u.

reject.- The reject filter removes elements that pass a certain test -- see bullets in this chapter section marked as (Test) for acceptable values. For example, for a list variable that contains [1,2,3,4,5] the loop statement with this filter {% for var in variable|reject("odd") %}{{var}}{% endfor %} -- where odd is the Jinja test -- rejects elements that are odd and thus its output is 2 and 4.

select.- The select filter selects elements that pass a certain test -- see bullets in this chapter section marked as (Test) for acceptable values. For example, for a list variable that contains [1,2,3,4,5] the loop statement with this filter {% for var in variable|select("odd") %}{{var}}{% endfor %} -- where odd is the Jinja test -- selects elements that are odd and thus its output is 1, 3 and 5.

slice.- The slice filter returns a slice of lists. For example, for a variable that contains ["Capuccino"] the filter statement {% for var in variable|slice(4) %}{{var}}{% endfor %} outputs ['C', 'a', 'p'],['u', 'c'],['c', 'i'], ['n', 'o']. It's possible to use the fill_with as a second argument -- which defaults to None -- so all segments contain the same number of elements filled with a given value. For example, {% for var in variable|slice(4,'FILLER') %}{{var}}{% endfor %} outputs: ['C', 'a', 'p'],['u', 'c','FILLER'],['c', 'i','FILLER'], ['n', 'o','FILLER'].

batch.- The batch filter returns a batch of lists. For example, a variable that contains ["Capuccino"] the filter statement {% for var in variable|batch(4) %}{{var}}{% endfor %} outputs ['C', 'a', 'p', 'u'],['c', 'c', 'i', 'n'],['o']. It's possible to use the fill_with as a second argument -- which defaults to None -- so all segments contain the same number of elements filled with a given value. For example, {% for var in variable|slice(4,'FILLER') %}{{var}}{% endfor %} outputs: ['C', 'a', 'p', 'u'],['c', 'c', 'i', 'n'],['o','FILLER','FILLER','FILLER'].

sort.- The sort filter sorts elements by ascending order. For example, if a variable contains ['e','u','a','i','o'] the statement {{variable|sort}} outputs ['a','e','i','o','u']. It's possible to indicate descending order by setting the first argument to true (e.g. {{variable|sort(true)}} outputs ['u','o','i','e','a']). In addition, if a list is made up strings, a second argument can be used to indicate case sensitiveness -- which is disabled by default -- to perform the sort operation (e.g. {{variable|sort(true,true)}}). Finally, if a list is composed of objects, it's also possible to specify the sort operation on a given attribute (e.g. variable|sort(attribute='date') to sort the elements based on the date attribute).


 
 
 
 
  
 

 
 
 
 
