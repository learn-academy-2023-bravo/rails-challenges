# Routes Controllers & Views

Create a rails app
`rails new routes_controllers_views_params -d postgresql -T`

Open folder
`cd routes_controllers_views_params`

Create database
`rails db:create`

Open code editor in folder
`code .`

Start Rails server
`rails s`

Generate a controller called Main
`rails g controller Main`

## Challenges

### As a user, I can visit a custom landing page at localhost:3000.

In `routes_controllers_views_params/config/routes.rb` add the following inside block:

```ruby
root to: 'main#index'
```

Create the view `routes_controllers_views_params/app/views/main/index.html.erb` with the following:

```erb
<h1>Welcome</h1>
```

Visit `http://127.0.0.1:3000` to see the welcome message

### As a user, I can see the names of my team members as hyperlinks on the landing page.

Add the following to `routes_controllers_views_params/app/views/main/index.html.erb`

```erb
<%= link_to 'Driver', '/driver' %>
<%= link_to 'Navigator', '/navigator' %>
```

### As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)

Create two methods in `main_controller.rb`

```ruby
def driver
    @name = 'Raymond'
    @top_three_things = ['Programming', 'Dogs', 'Gym']
end

def navigator
    @name = 'Nikki'
    @top_three_things = ['Music', 'Movies', 'Photography']
end
```

Create two views in `routes_controllers_views_params/app/views/main` with the following names:

- `driver.html.erb`
- `navigator.html.erb`

In `driver.html.erb` and `navigator.html.erb` add the following:

```erb
<h1><%= @name %></h1>

<ul>
    <% @top_three_things.each do |value| %>
        <li><%= value %></li>
    <% end %>
</ul>
```

Add the following routes inside `routes_controllers_views_params/config/routes.rb`:

```ruby
get '/driver' => 'main#driver'
get '/navigator' => 'main#navigator'
```

### As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.

Create controller
`rails g controller cubed`

Run server
`rails s`

Add method to controller

```ruby
def cube
  @cube = params[:number].to_i ** 3
end
```

Create view called `cube.html.erb`

```ruby
<h1>cube</h1>
<p><%= @cube %></p>
```

Create new route

```ruby
get '/cube/:number' => 'cubed#cube'
```

### As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.

Add controller method

```ruby
def evenly
  num1 = params[:num1]
  num2 = params[:num2]
  @is_evenly = num1 % num2 == 0
end
```

Add route

`get '/evenly/:num1/:num2' => 'main#evenly'`

Create view

```ruby
<h1>Evenly</h1>
<p><%= @is_evenly %></p>
```

### As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).

Create method

```ruby
def palindrome
  @is_palindrome = params[:string].downcase == params[:stirng].downcase.reverse
end
```

Create route

```ruby
get '/palindrome/:string' => 'main#palindrome'
```

Create view

```ruby
<h1>Palindrome</h1>
<%= @is_palindrome %>
```

### As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.

Create method

```ruby
def madlib
  @verb = params[:verb]
  @noun = params[:noun]
  @adjective = params[:adjective]
  @adverb = params[:adverb]

  @silly_story = "The day I saw the Monkey King #{@verb} was one of the most interesting days of the year. After he did that, the king played chess on his brother's #{@noun} and then combed his #{@adjective} hair with a comb made out of old fish bones. Later that same day, I saw the Monkey King dance #{@adverb} in front of an audience of kangaroos and wombats."
end
```

Create route

```ruby
get '/madlib/:verb/:noun/:adjective/:adverb' => 'main#madlib'
```

Create view

```ruby
<h1>Madlib</h1>
<%= @silly_story %>
```
