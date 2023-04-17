As a developer, I need username, password, and email to be required.

As a developer, I need every username to be at least 5 characters long.
As a developer, I need each username to be unique.
As a developer, I need each password to be at least 6 characters long.
As a developer, I need each password to be unique.
As a developer, I want my Account model to have many associated Addresses.
As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.
As a developer, I want to validate the presence of all fields on Address.


create_table "accounts", force: :cascade do |t|
    t.string "username"
    t.string "password"
    t.string "email"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  create_table "addresses", force: :cascade do |t|
    t.integer "street_number"
    t.string "street_name"
    t.string "city"
    t.string "state"
    t.integer "zip"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.integer "account_id"
  end

end

RSpec.describe Account, type: :model do
  it "requires a username" do 
    name = Account.create(password:'opensesame',email:'greg@gmail.com')
    expect(name.errors[:username]).to_not be_empty
  end
  it "requires a password" do
    name = Account.create(username:'gregapple', email:'greg@gmail.com')
    expect(name.errors[:password]).to_not be_empty
  end
  it "requires an email" do
    name = Account.create(username:'gregapple', password:'opensesame')
    expect(name.errors[:email]).to_not be_empty
  end
  it 'username is at least 5 characters long' do
    name = Account.create(username:'XZ', password:'opensesame', email:'greg@gmail.com')
    expect(name.errors[:username]).to_not be_empty
  end
  it 'username is unique' do
    name = Account.create(username: 'summer', password:'winter', email:'spring@gmail.com')
    unique = Account.create(username: 'summer', password:'winter', email:'spring@gmail.com')
    expect(unique.errors[:username]).to_not be_empty
  end
  it 'password is at least 6 characters long' do
    name = Account.create(username: 'gregapple', password:'GB', email:'go@gmail.com')
    expect(name.errors[:password]).to_not be_empty
  end
  it 'password is unique' do 
    name = Account.create(username:'basketball', password:'football', email:'baseball@gmail.com')
    balls = Account.create(username:'basketball', password:'football', email:'baseball@gmail.com')
    expect(balls.errors[:password]).to_not be_empty
  end

end

RSpec.describe Address, type: :model do
  it "has valid street name" do
    location = Address.create(street_number:4532, city:'San Diego', state:'CA', zip: 92118)
    expect(location.errors[:street_name]).to_not be_empty
  end
  it 'has a valid street number' do
    location = Address.create(street_name:'elm street', city:'San Diego', state:'CA', zip: 92118)
    expect(location.errors[:street_number]).to_not be_empty
  end
  it 'has a valid city' do
    location = Address.create(street_number:4532, street_name:'elm street', state:'CA', zip: 92118)
    expect(location.errors[:city]).to_not be_empty
  end
  it 'is a valid state' do
    location = Address.create(street_number:4532, street_name:'elm street', city:'San Diego', zip: 92118)
    expect(location.errors[:state]).to_not be_empty
  end
  it 'has a valid zip' do
    location = Address.create(street_number:4532, street_name:'elm street', city:'San Diego', state:'CA')
    expect(location.errors[:zip]).to_not be_empty
  end 
  end

  class Account < ApplicationRecord
    has_many :addresses
    validates :username, :password, :email, presence: true
    validates :username, length: {minimum: 5}
    validates :username, uniqueness: true
    validates :password, length: {minimum: 6}
    validates :password, uniqueness: true
end
class Address < ApplicationRecord
    belongs_to :account
    validates :street_name, presence: true
    validates :street_number, presence: true
    validates :city, presence: true
    validates :state, presence: true
    validates :zip, presence: true

    
end