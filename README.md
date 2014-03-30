Add tabs to a product description or page or srticle on shopify
===============================================================
Step-1:
Go your product page and enter the below text on your editor:

[[start]]
DESCRIPTION
this is description
[[end]]

 [[start]]
FEATURE
this is feature
[[end]]

 [[start]]
SPECIFICATION
this is sepecificaiton
[[end]]

 [[start]]
EXTRA SPECIFICATION
this is extra sepecificaiton
[[end]]

[[start]]
OTHER
this is other
[[end]]

 
[[start]]
More
this is other
[[end]]



Step-2: Be sure that the tab titles (e.g. 'DESCRIPTION') are entered as 'Heading 1' text

step-3: Add below code where you want to show your tab.
  {% assign split_word = product.description  | remove:'[[start]]' %}
        {% assign words = split_word | split: '[[endtab]]'%}
          
          {% assign test=words.size|minus:2%}
          
          {% for word in words limit:test offset:1%}
          
           {% assign split_word_word = word | remove: '<h1>'  %}
          {% assign split_word_words = split_word_word | split: '</h1>'| first  %}
        
          {% for w in split_word_words  %}
          {% assign split_word_word_title = w | strip_html  %}
          {% assign temp= i|plus:1 %}
          <a href="" data-child="resource{{temp}}" class="tab"> {{split_word_word_title}}</a>
          {% assign i=temp %}
        
          {%endfor%}
          
        {%endfor%}
