Challenges

Params

# As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.
file: main_controller.rb

```ruby

 def cubed
        @number = params[:number]
        @result = @number.to_i ** 3
    end

```

file: cubed.html.erb

```ruby
<h1>Number cubed</h1>

<h3>result: <%= @result %> </h3>

<%= link_to "Back to Landing Page", "/landing" %>
```


file: landing.html.erb

```ruby

<h1>Hello, welcome to our team page.</h1>
<h3>Please visit our team member links to see their fave restaurants.</h3>


<%= link_to "Apple", "/team_member_1" %>
<br/>

<%= link_to "James", "/team_member_2" %>
<br/>

<%= link_to "Kevin", "/team_member_3" %>
<br/>

<%= link_to "Number Cubed", "/cubed" %>
<br/>

<%= link_to "Number evenly divisble", "/evenly" %>
<br/>

<%= link_to "Word is a palindrome?", "/palindrome" %>
<br/>




```


file: routes.rb

```ruby

Rails.application.routes.draw do

  get 'team_member_1' => 'main#team_member_1'
  get 'team_member_2' => 'main#team_member_2'
  get 'team_member_3' => 'main#team_member_3'

  get 'cubed/:number' => 'main#cubed'
  get 'evenly/:number1/:number2' => 'main#evenly'
  get 'palindrome/:string' => 'main#palindrome'
  

  get '/landing' => 'main#landing'
  root 'main#landing'
end


```

# As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.
```ruby

 def evenly 
        @number1 = params[:number1]
        @number2 = params[:number2]
        @result1 = @number1.to_i / @number2.to_i
    end

```

file: evenly.html.erb
```ruby

<h1>Number divisible by second number</h1>

<h3>result: <%= @result1 %> </h3>

<%= link_to "Back to Landing Page", "/landing" %>

```


# As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).
```ruby

    def palindrome
        @string = params[:string]
        if @string == @string.reverse
           @result2 = "#{@string} is a palindrome"
        else 
            @result2 = "#{@string} is not a palindrome"
        end
    end

```

file: palindrome.html.erb
```ruby
<h1>Is this word a palindrome?</h1>
<h3>result: <%= @result2 %> </h3>


<%= link_to "Back to Landing Page", "/landing" %>
```

# As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.