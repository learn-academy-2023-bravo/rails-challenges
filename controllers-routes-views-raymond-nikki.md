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
