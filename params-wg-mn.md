<h1> Welcome to our app page <h2>
<%= link_to "cubed", "/cubed" %>

<h1> Palindrome Checker </h1>

<h2> <%= @result %> </h2>

class MainController < ApplicationController
    def cubed 

        if @number = params[:number].to_i
        @result = @number ** 3
        elsif @number == nil 
            @result = "please enter a number"
        end
    end
    def evenly 
        @number1 = params[:number1].to_i
        @number2 = params[:number2].to_i
        if @number2 == 0
            @result = "error"
        elsif
         @number1 % @number2 == 0 
            @result = "#{@number1} is evenly divisible by #{@number2}"
        elsif
            @result = "#{@number1} is not evenly divisible by #{@number2}"
        else
        @result = "Cannot divide by 0" 
        end
    end

    def palindrome 
        @word = params[:word]
        if @word.downcase == @word.reverse.downcase
            @result = "#{@word} is a palindrome"
        elsif 
            @result = "#{@word} is not a palindrome"
        end
    end

    def madlib
        @noun = params[:noun]
        @verb = params[:verb]
        @adjective = params[:adjective]
        @adverb = params[:adverb]
    end
    def landing
    end



end


<h1> Madlib Story </h1>
<p> Once upon a time, there was a <%= @adjective %> <%= @noun %> who loved to <%= @verb %> <%= @adverb %>. </p>

<h1> Cubed Calculator </h1>
<h3> Your Number  <%= @number %> </h3>
<h4> Result   <%= @result %> </h4> 

<h1> Evenly Calculator <h1>

<h2> Result: <%= @result %> </h2>

Rails.application.routes.draw do
get '/cubed/:number' => 'main#cubed'
get '/evenly/:number1/:number2' => 'main#evenly'
get '/palindrome/:word' => 'main#palindrome'
get '/madlib/:adjective/:noun/:verb/:adverb' => "main#madlib"
get '/landing' => "main#landing"
root to: "main#landing" 
end