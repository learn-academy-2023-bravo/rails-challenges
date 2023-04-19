Challenges
Routes, Views, Controllers

# As a user, I can visit a custom landing page at localhost:3000.
 - see below
# As a user, I can see the names of my team members as hyperlinks on the landing page.


file: landing.html.erb

<h1>Hello, welcome to our team page.</h1>
<h3>Please visit our team member links to see their fave restaurants.</h3>


<%= link_to "Apple", "/team_member_1" %>
<br/>

<%= link_to "James", "/team_member_2" %>
<br/>

<%= link_to "Kevin", "/team_member_3" %>
<br/>

team_member_1.html.erb
<h1>Here are Apples favorite restaurants.</h1>

<p> <%= @favorites %> </p>


<ul> 
    <% @restaurants.each do |value| %>
    <li> <%= value %> </li>
    <% end %>
</ul>

<%= link_to "Back to Landing Page", "/landing" %>



# As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)

files: main_controller.rb

```ruby

    def team_member_1
        @favorites = 'Here is team member 1 favorite restaurants'
        @restaurants = ["Crab Shack", "Guelaguetza", "Taco Bell"]

    end

    def team_member_2
        @favorites = 'Here is team member 2 favorite restaurants'
        @restaurants = ["Olive Garden", "Jeune et Jolie", "Taco Bell"]

    end

    def team_member_3
        @favorites = 'Here is team member 3 favorite restaurants'
        @restaurants = ["Purina Cat Chow", "Cat Nip", "Fancy Feast"]

    end


    def landing
    end

end
```

file: routes.rb

```ruby

  get 'team_member_1' => 'main#team_member_1'
  get 'team_member_2' => 'main#team_member_2'
  get 'team_member_3' => 'main#team_member_3'

  get '/landing' => 'main#landing'
  root 'main#landing'
end

```