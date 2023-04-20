Routes, Views, Controllers

# As a user, I can visit a custom landing page at localhost:3000.

# home_contoller.rb:
class HomeController < ApplicationController
    def landing
    end
    def sam
        @sam_favorites = ['Pasta', 'Movies', 'Dogs']
    end
    def demario
        @demario_favorites = ['Food', 'Games', 'Indoors']
    end
    def jose
        @jose_favorites = ['Food', 'Books', 'Dogs']
    end
end


# routes.rb:
Rails.application.routes.draw do
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"

  get '/landing' => 'home#landing'
  get '/sam' => 'home#sam'
  get '/jose' => 'home#jose'
  get '/demario' => 'home#demario'
  root'home#landing'

end


# As a user, I can see the names of my team members as hyperlinks on the landing page.

# landing.html.erb:
<p> Landing Page </p>
<%= link_to "Sam", "/sam" %>
<br/>
<%= link_to "DeMario", "/demario" %>
<br/>
<%= link_to "Jose", "/jose" %>

As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)

# sam.html.erb:
<ul>
    <% @sam_favorites.each do |value| %>
        <li> <%= value %> </li>
    <% end %>
</ul>

# demario.html.erb:
<ul>
    <% @demario_favorites.each do |value| %>
        <li> <%= value %> </li>
    <% end %>
</ul>

# jose.html.erb:
<ul>
    <% @jose_favorites.each do |value| %>
        <li> <%= value %> </li>
    <% end %>
</ul>