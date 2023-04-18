main_controller.rb
________________________________

class MainController < ApplicationController
    def landing
        render 'landing'
    end
    def jake
        @name1 = 'Jake'
        render 'jake'
    end
    def jake_three
        render 'jake_three'
    end
    def spencer
        @name2 = 'Spencer'
        render 'spencer'
    end
    def spencer_three
        render 'spencer_three'
    end
    def cubed 
        @number = (params[:number].to_i)
        render 'cubed'
    end
    def evenly 
        @first = (params[:number].to_i)
        @second = (params[:number2].to_i)
        if params[:number].to_i % params[:number2].to_i == 0
            @result = "#{@first} is divisible by #{@second} " 
        else
            @result = "#{@first} is not divisible by #{@second} "
        end
        render 'evenly'
    end
    def palindrome
        @string = params[:string]
        if params[:string].downcase == params[:string].downcase.reverse 
            @result = "#{@string} is a PALINDROME!"
        else
           @result = "#{@string} is NOT a pal-in-drome..."
        end
    end
    def madlib
        @noun = params[:string1]
        @verb = params[:string2]
        @adjective = params[:string3]
        @adverb = params[:string4]
        # @word = params[:string1, :string2, :string3, :string4]
        @result = "Once upon a time there was a large #{@noun} that could #{@adverb} #{@verb} like a #{@adjective}."
        render 'madlib'
    end
end

________________________________
routes.rb
________________________________

Rails.application.routes.draw do
  root to: 'main#landing'
  get '/landing' => 'main#landing'
  get '/jake' => 'main#jake'
  get '/jake_three' => 'main#jake_three'
  get '/spencer_three' => 'main#spencer_three'
  get '/cubed/:number' => 'main#cubed'
  get '/evenly/:number/:number2' => 'main#evenly'
  get '/palindrome/:string' => 'main#palindrome'
  get '/madlib/:string1/:string2/:string3/:string4' => 'main#madlib'
end

__________________________________
landing.html.erb
__________________________________

<h1> Landing Page </h1>
<br/>
<%= link_to 'Jake', '/jake_three' %>
<br/>

<%= link_to 'Spencer', '/spencer_three' %>
<br/>
<%= link_to 'Cubed', '/cubed' %>
<br/>
<%= link_to 'Evenly', '/evenly' %>

<br/>
<%= link_to 'Palindrome', '/palindrome' %>
<br/>
<%= link_to 'Madlibs', '/madlib' %>

____________________________________
cubed.html.erb
____________________________________

<h1> Cubed Numbre </h1>
<br/>
<p> <%= @number ** 3%></p>

_____________________________________
evenly.html.erb
_____________________________________

<h1> Divide by </h1>
<br/>

<p> <%= @result =%> </p>

_____________________________________
jake_three.html.erb
_____________________________________

<h1> TEAM NAMES </h1>
<br/>
<p> <%= @name1 %>1. Puppies 2. Hiking 3. Longboarding</p>

______________________________________
madlib.html.erb
______________________________________

<h1> Story Time with Jake </h1>
<br/>

<p> <%= @result =%> </p>

_____________________________________
palindrome.html.erb
_____________________________________

<h1> pALiNdroME </h1>
<br/>

<p> <%= @result =%> </p>

______________________________________
spencer_three.html.erb
______________________________________

<h1> TEAM NAMES </h1>
<br/>
<p> <%= @name2 %>1. food 2. sleep 3. more food</p>