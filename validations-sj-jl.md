Create a Rails application called company_contacts. The app will have a PostgreSQL database.
<!-- rails new company_contacts -d postgresql -T -->

Generate a model called Account that has a username, a password, and an email.
<!-- - rails generate model Account username:string password:string email:string -->

All stories should have accompanying model specs.

<!-- -require 'rails_helper'

RSpec.describe Account, type: :model do
  it 'is not valid without a username' do
    learn_student = Account.create password: 'password', email: 'stundent@learnacademy.com'
    expect(learn_student.errors[:username]).to_not be_empty
  end -->



Developer Stories

As a developer, I need username, password, and email to be required.

<!-- RSpec.describe Account, type: :model do
  it 'is not valid without a username' do
    learn_student = Account.create password: 'password', email: 'stundent@learnacademy.com'
    expect(learn_student.errors[:username]).to_not be_empty
  end
  it 'is not valid without a password' do
    learn_student = Account.create username:"James_Lee", email: 'stundent@learnacademy.com'
    expect(learn_student.errors[:password]).to_not be_empty
  end
  it 'is not valid without a email' do
    learn_student = Account.create username:"Spencer_Johnson", password: 'password'
    expect(learn_student.errors[:email]).to_not be_empty
  end
end -->


As a developer, I need every username to be at least 5 characters long.
As a developer, I need each username to be unique.

<!-- it 'is not valid unless username is atleast 5 characters' do
    learn_student = Account.create username:"Sp", password: 'password', email:"student@learnacademy.com"
    expect(learn_student.errors[:username]).to_not be_empty
  end
  it 'does not allow duplicate usernames' do
    learn_student = Account.create username:"Spencer_Johnson", password: 'password', email:"student@learnacademy.com"
    expect(learn_student.errors[:username]).to_not be_empty
  end -->


As a developer, I need each password to be at least 6 characters long.
As a developer, I need each password to be unique.

<!-- it 'is not valid unless password is atleast 6 characters' do
    learn_student = Account.create username:"Sp", password: 'password', email:"student@learnacademy.com"
    expect(learn_student.errors[:password]).to_not be_empty
  end
  it 'does not allow duplicate passwords' do
    learn_student = Account.create username:"Spencer_Johnson", password: 'password', email:"student@learnacademy.com"
    expect(learn_student.errors[:password]).to_not be_empty
  end -->


As a developer, I want my Account model to have many associated Addresses. 

<!-- class Account < ApplicationRecord
    validates :username, :password, :email, presence: true
    validates :username, length: { minimum: 5 }
    validates :username, uniqueness: true
    validates :password, length: { minimum: 6 }
    validates :password, uniqueness: true
    has_many :addresses
end
class Address < ApplicationRecord
    belongs_to :accounts
end -->


As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.

<!-- rails generate model Address street_number:integer street_name:string city:string state:string zipcode:integer 
      invoke  active_record
      create    db/migrate/20230417221441_create_addresses.rb
      create    app/models/address.rb
      invoke    rspec
      create      spec/models/address_spec.rb
rails db:migrate -->


As a developer, I want to validate the presence of all fields on Address.
