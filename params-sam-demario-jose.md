Params

As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.

# in home_controller.rb:
def cubed
        @result = (params[:number].to_i ** 3)
end

# in cubed.html.erb
<h1>
    Cubed Number is: <%= @result %>
</h1>

As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.

# in home_controller.rb:
def evenly
        if params[:num1].to_i % params[:num2].to_i == 0
            @result = 'is evenly divisible'
        else
            @result = 'is not evenly divisible'
        end
end

# in evenly.html.erb
<h1>
    <%= params[:num1] %> <%= @result %> by <%= params[:num2] %>
</h1>

As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).

# in home_controller.rb:
def palindrome
        if params[:string].reverse == params[:string]
            @result = 'is a palindrome'
        else
            @result = 'is not a palindrome'
        end
end

# in palindrome.html.erb:
<h1>
    <%= params[:string] %> <%= @result %>
</h1>

As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.

# in home_controller.rb:
def madlib
        @story = "DeMario grabbed the #{params[:adjective]} #{params[:noun]} and #{params[:verb]} away #{params[:adverb]}."
end

# in madlib.html.erb:
<h1>
    <%= @story %>
</h1>